---
title: 'ACSD-52287: 보관된 주문의 상태가 변경되지 않음'
description: ACSD-52287 패치를 적용하여 대변 메모가 제출된 후 그리드에서 보관된 주문의 상태가 *완료됨*에서 *마감됨*으로 변경되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Checkout
role: Admin, Developer
exl-id: c88c5c87-eec7-4105-9e4e-815d0888a34b
source-git-commit: 178023177975f210ebf7dd07e8c75cfe3ac89ff1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-52287: 보관된 주문의 상태가 변경되지 않음

ACSD-52287 패치는에서 보관된 주문의 상태가 변경되지 않는 문제를 해결합니다. *완료됨* 끝 *종료됨* 대변 메모가 제출된 후의 그리드에서. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38이 설치되었습니다. 패치 ID는 ACSD-52287입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

보관된 주문의 상태는에서 변경되지 않습니다. *완료됨* 끝 *종료됨* 대변 메모가 제출된 후의 그리드에서.

<u>재현 단계</u>:

1. 구성 *[!UICONTROL Asynchronous Indexing]*.
   * 관리 사이드바에서 다음 위치로 이동하십시오. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * 왼쪽 패널에서 를 확장합니다. **[!UICONTROL Advanced]** 섹션 및 선택 **[!UICONTROL Developer]** 밑에.
   * 확장 **[!UICONTROL Grid Settings]** 섹션.
   * 설정 *[!UICONTROL Asynchronous indexing]* 끝 *예*.
   * 클릭 **[!UICONTROL Save Config]**.
1. 구성 *[!UICONTROL Order Archive]*.
   * 관리 사이드바에서 다음 위치로 이동하십시오. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * 왼쪽 패널에서 를 확장합니다. **[!UICONTROL Sales]** 섹션 및 선택 **[!UICONTROL Sales]** 밑에.
   * 확장 **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** 섹션.
   * 설정 *[!UICONTROL Enable Archiving]* 끝 *예* (나머지 구성은 기본값으로 둡니다.)
   * 클릭 **[!UICONTROL Save Config]**.
1. 프론트 엔드에 주문을 넣으세요.
1. 실행 [!DNL cron]  을 참조하십시오. *[!UICONTROL Admin Order Grid]*.
1. 주문 상태를 갱신하려면 송장 발행 및 주문 출하 *완료*.
1. 실행 [!DNL cron]  을(를) 업데이트하려면 *[!UICONTROL Sales Order Grid]* (최신 주문 상태 포함)
1. 주문을 보관합니다.
1. 로 이동 *[!UICONTROL Archived order grid]*.
1. 보관된 주문을 열고 다음을 만들어 오프라인으로 주문을 환불합니다. [!UICONTROL Credit Memo] 만들기 [!UICONTROL Order status]: *종료됨*.
1. 실행 [!DNL cron] 몇 번.
1. 다음 확인: *[!UICONTROL Archived order grid]* (새 주문 상태)

<u>예상 결과</u>:

순서는 로 표시됩니다. *종료됨*.

<u>실제 결과</u>:

순서는 로 표시됩니다. *완료*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
