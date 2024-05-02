---
title: '''ACSD-51857: ''aggregate_sales_report_bestsellers_data''의 느린 cron 작업이 성능에 영향을 미침'''
description: ACSD-51857 패치를 적용하여 느린 cron 작업 'aggregate_sales_report_bestsellers_data'가 큰 'sales_order' 및 'sales_order_item' 데이터베이스 테이블에 영향을 주는 Adobe Commerce 문제를 해결합니다.
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857: 크론 작업이 느림 `aggregate_sales_report_bestsellers_data` 성능에 영향을 미침

ACSD-51857 패치를 사용하면 cron 작업이 느려지는 문제가 해결됩니다 `aggregate_sales_report_bestsellers_data` 크게 영향 `sales_order` 및 `sales_order_item` 데이터베이스 테이블. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34가 설치되어 있습니다. 패치 ID는 ACSD-51857입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

의 Cron 작업 성능 `aggregate_sales_report_bestsellers_data` 느림 `sales_order` 및 `sales_order_item` 데이터베이스 테이블.

이 문제를 해결하기 위해 보고서의 데이터를 가져오는 기본 데이터 쿼리가 더 효율적인 양식으로 다시 작성되었습니다. 이제 하위 쿼리를 사용하여 데이터 하위 집합을 결정합니다.

하위 쿼리가 최대한 빨리 작동하도록 하기 위해 `sales_order` 데이터베이스 테이블: `SALES_ORDER_STORE_STATE_CREATED` 기준 `store_id`, `state`, 및 `created_at` 열.

<u>전제 조건</u>

매일 많은 주문을 확인하십시오.

<u>재현 단계</u>

1. 실행 `aggregate_sales_report_bestsellers_data` cron job.
1. 관리자 대시보드의 아래 아래에 표시할 데이터를 선택합니다. **[!UICONTROL Bestsellers]** 탭.

<u>예상 결과</u>:

*[!UICONTROL Quantity per source]* 다음 아래에 **[!UICONTROL Configuration]** 탭은 비워둘 수 없습니다.

<u>실제 결과</u>:

*[!UICONTROL Quantity per source]* 다음 아래에 **[!UICONTROL Configuration]** 탭이 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
