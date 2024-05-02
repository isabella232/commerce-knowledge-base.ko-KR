---
title: 데이터베이스의 변경 사항은 상점 앞에 반영되지 않습니다
description: 이 문서에서는 엔티티 업데이트가 적용되지 않도록 지연 또는 중단을 방지하는 솔루션을 제공합니다. 여기에는 변경 로그 테이블의 크기가 커지지 않도록 하는 방법과 MySQL 테이블 트리거를 설정하는 방법이 포함됩니다.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# 데이터베이스의 변경 사항은 상점 앞에 반영되지 않습니다

이 문서에서는 엔티티 업데이트가 적용되지 않도록 지연 또는 중단을 방지하는 솔루션을 제공합니다. 여기에는 변경 로그 테이블의 크기가 커지지 않도록 하는 방법과 MySQL 테이블 트리거를 설정하는 방법이 포함됩니다.

영향을 받는 제품 및 버전:

* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x
* Adobe Commerce 온-프레미스 2.2.x, 2.3.x

## 문제

데이터베이스에서 변경한 사항이 상점 앞에 반영되지 않거나 엔티티 업데이트 적용이 크게 지연됩니다. 영향을 받을 수 있는 개체에는 제품, 범주, 가격, 재고, 카탈로그 규칙, 판매 규칙 및 대상 규칙이 포함됩니다.

## 원인

인덱서가 다음과 같은 경우 [일정별로 업데이트하도록 구성됨](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers), 변경 로그가 너무 크거나 MySQL 트리거가 설정되지 않은 하나 이상의 테이블로 인해 문제가 발생할 수 있습니다.

### 크기가 큰 변경 로그 테이블

다음과 같은 경우 변경 로그 테이블이 크게 증가합니다. `indexer_update_all_views` cron 작업이 여러 번 완료되지 않았습니다.

변경 로그 테이블은 엔티티에 대한 변경 사항이 추적되는 데이터베이스 테이블입니다. 레코드는 변경이 적용되지 않는 한 변경 로그 테이블에 저장됩니다. 단, 이 작업은 `indexer_update_all_views` cron job. Adobe Commerce 데이터베이스에는 여러 변경 로그 테이블이 있으며, 예를 들어 INDEXER\_TABLE\_NAME + &#39;\_cl&#39; 패턴에 따라 이름이 지정됩니다. `catalog_category_product_cl`, `catalog_product_category_cl`. 데이터베이스에서 변경 사항을 추적하는 방법에 대한 자세한 내용은 [색인화 개요 > Mview](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview) 개발자 설명서에 있는 문서입니다.

### MySQL 데이터베이스 트리거가 설정되지 않음

엔티티(제품, 카테고리, 대상 규칙 등)를 추가하거나 변경한 후 해당 변경 로그 테이블에 레코드가 추가되지 않는 경우 데이터베이스 트리거가 설정되지 않은 것으로 의심됩니다.

## 솔루션

>[!WARNING]
>
>조작을 수행하기 전에 데이터베이스 백업을 만들고 사이트 로드가 많은 기간 동안에는 이를 피하는 것이 좋습니다.

### 변경 로그 테이블의 크기가 너무 커지지 않도록 합니다.

다음을 확인합니다. `indexer_update_all_views` cron 작업이 항상 성공적으로 완료되었습니다.

다음 SQL 쿼리를 사용하여 실패한 모든 인스턴스를 가져올 수 있습니다. `indexer_update_all_views` cron 작업:

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

또는 를 검색하여 로그에서 해당 상태를 확인할 수 있습니다. `indexer_update_all_views` 항목:

* `<install_directory>/var/log/cron.log` - 버전 2.3.1+ 및 2.2.8+의 경우
* `<install_directory>/var/log/system.log` - 이전 버전의 경우

### MySQL 테이블 트리거 다시 설정

누락된 MySQL 테이블 트리거를 설정하려면 인덱서 모드를 다시 설정해야 합니다.

1. &#39;저장 시&#39;로 전환합니다.
1. &#39;일정에 따라&#39;로 다시 전환합니다.

다음 명령을 사용하여 이 작업을 수행합니다.

>[!WARNING]
>
>인덱서 모드를 전환하기 전에 웹 사이트를 추가하는 것이 좋습니다. [유지 보수](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode) 모드 및 [cron 작업 비활성화](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs) 데이터베이스 잠금을 방지합니다.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>인덱서 모드가 예약으로 설정되어 있으면 인덱서 관련 데이터베이스 트리거가 추가되고, 인덱서 모드가 실시간으로 설정되어 있으면 제거됩니다. 인덱서가 예약되도록 설정되어 있는 동안 트리거가 데이터베이스에서 누락된 경우 인덱서를 실시간으로 변경한 다음 다시 예약으로 변경합니다. 그러면 트리거가 재설정됩니다.

## 관련 읽기

<ul><li title="MySQL 테이블이 너무 큽니다."><a href="/help/troubleshooting/database/mysql-tables-are-too-large.md">MySQL 테이블이 너무 큽니다.</a> 을 참조하십시오.</li>
<li title="MySQL 테이블이 너무 큽니다."><a href="https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview">인덱서 개요 &gt; Mview</a> 개발자 설명서에서 확인할 수 있습니다.</li></ul>
