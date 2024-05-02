---
title: 'MDVA-32655: "quoteItemCleaner" 소비자가 실행당 하나의 메시지를 실행합니다.'
description: MDVA-32655 패치는 여러 제품을 삭제한 후 소비자 'quoteItemCleaner'에 대한 잘못된 "진행 중" 메시지 상태를 올바른 "완료" 메시지로 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치된 경우 사용할 수 있습니다. 패치 ID가 32655. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 07213430-f779-4a53-89fd-bc3905e13675
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32655: &quot;quoteItemCleaner&quot; 소비자는 실행당 하나의 메시지를 실행합니다.

MDVA-32655 패치는 잘못된 &quot;진행 중&quot; 메시지 상태를 소비자의 올바른 &quot;완료&quot; 메시지로 수정합니다 `quoteItemCleaner` 여러 제품을 삭제한 후 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치되었습니다. 패치 ID가 32655. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.3.3

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음 `quoteItemCleaner` 소비자는 각 실행 시 하나의 메시지만 실행합니다.

<u>재현 단계</u>:

1. 다음 확인: `queue_message_status` 데이터베이스 테이블 및 기존의 모든 대기열 메시지가 &quot;완료&quot; 상태에 있는지 확인합니다(상태 ID 4).
1. 자동 Adobe Commerce cron 실행을 중지합니다.
1. 두 개 또는 세 개의 간단한 제품을 만듭니다.
1. 이 세 가지 간단한 제품을 대량으로 삭제합니다.
1. 다음에서 `queue_message_status` 표 다음에 대한 세 개의 새 레코드가 있습니다. `catalog_product_removed_queue` 상태 ID 2의 주제(새 레코드).
1. 다음 명령을 실행하여 이러한 보류 중인 작업을 처리합니다. `catalog_product_removed_queue` 메시지:

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u>예상 결과</u>:

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

모두 `catalog_product_removed_queue` 메시지 상태가 완료되도록 업데이트됩니다(ID=4).

<u>실제 결과</u>:

셋 중 하나의 레코드만 &quot;완료&quot; 상태로 업데이트됩니다(ID = 4). 다른 두 메시지의 상태는 상태 ID = 3(진행 중)입니다. 처리되지 않은 대기열 메시지가 있는 백로그가 생성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
