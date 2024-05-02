---
title: 색인이 무효화되고 'indexer_reindex_all_invalid'가 계속 실행됩니다.
description: 색인이 무효화되고 'indexer_reindex_all_invalid'가 계속 실행됩니다.
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# 색인이 무효화되고 `indexer_reindex_all_invalid` 지속적으로 실행

이 문서에서는 지속적인 리인덱싱으로 인해 사이트에 성능 문제가 발생하는 경우 이 문제에 대해 가능한 해결 방법을 제공합니다. 이 문제는 다음으로 인해 발생합니다. [!DNL cron] 작업 `indexer_reindex_all_invalid` 연속 실행 및 캐시 정리 [!DNL reindex].

## 영향을 받는 제품 및 버전

* Adobe Commerce (cloud 및 온프레미스) 2.4.0+ (As **[!UICONTROL Category Permissions]** 는 Adobe Commerce 전용 기능이며 Magento Open Source에 영향을 주지 않습니다.)

## 문제

위치 [!DNL New Relic One] 오류 로그가 표시되어야 함 `indexer_update_all_views` 1초 이상의 시간으로 여러 번 실행(즉, 무언가를 처리하는 중).

## 원인

핵심 Adobe Commerce 임포터가 실행될 때(수동으로 또는 다음을 통해) [!DNL cron]) 그런 다음 여러 코어 모듈에 있는 플러그인 세트를 실행하여 무효화해야 할 인덱스를 결정합니다.

이 문제는 다음 경우에 발생합니다. **[!UICONTROL Category Permissions]** 모듈이 [!DNL Commerce Admin]. true인 경우 모듈의 플러그인은 가져오기가 실행될 때 항상 제품 및 카테고리 색인(및 연결된 색인)을 무효화합니다. 표준 가져오기 유형을 검사하면 모두 **[!UICONTROL Category Permissions]**. 무효화가 예상됩니다.

또한 사이트에 B2B 모듈이 활성화되어 있는 경우 **[!UICONTROL Shared Catalog]** 활성화됨, 켜짐 및 잠김 **[!UICONTROL Category Permissions]**. 끄기 **[!UICONTROL Shared Catalog]** 잠금 해제됨 **[!UICONTROL Category Permissions]**, 하지만 끄지 마십시오.

<u>확인 중 [!DNL cron] 로그인 [!DNL MySQL] 데이터베이스</u>:

에 로그인하는 경우 [!DNL MySQL] 데이터베이스를 통해 다음을 확인할 수 있습니다. `cron` 에 대한 로그 **[!DNL reindex all indexes]** 프로세스.
이 **다음과 같아야 함** 여러 번 나타나지만 중요한 요소는 그 과정이 두 가지 가능한 일 중 하나를 한다는 것이다.

프로세스는 다음 두 가지 중 하나만 수행할 수 있습니다.

1. Nothing: 0초에서 1초(1초 이하) 정도 소요됩니다. 프로세스는 수행해야 할 작업이 있는지 확인한 후, 필요하지 않은 경우 중지합니다.
1. [!DNL Reindex] 모두: 항상 시간이 소요됩니다(일반적으로 분).

일반적으로 실행 시간이 1초 미만인 상태에서 많은 프로세스가 발생하는 것을 보고자 합니다.
따라서 상인은 이를 사용할 수 있습니다 [!DNL MySQL] 다음 작업을 수행하는 트랜잭션을 찾기 위한 쿼리 **1초 이상** 실행하려면:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

다음을 실행하여 기간이 얼마나 오래 기록되는지 볼 수 있습니다.

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

만약 이것이 적절한 평가를 할 수 있는 충분한 기간을 주지 않는다면, 당신은 성공적인 시간을 증가시킬 수 있다 `cron` 프로세스는 이 작업 다음에 로그에 유지됩니다. [[!DNL Cron] (예약된 작업)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 안내선 및 증가 **[!DNL Success History Lifetime]** 값(기본값은 60분)입니다.


## 솔루션

확장 `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` 따라서 `afterImportSource` 메서드에서 사용자 지정 가져오기를 제외합니다.

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

위치 `ENTITY_CODE` 는 의 엔티티 이름 매개 변수에 사용되는 값입니다. `import.xml` 사용자 지정 가져오기용 파일입니다.

## 관련 읽기

[구성 [!DNL cron] 작업](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) Adobe Commerce 작업 구성 안내서에서 참조할 수 있습니다.
