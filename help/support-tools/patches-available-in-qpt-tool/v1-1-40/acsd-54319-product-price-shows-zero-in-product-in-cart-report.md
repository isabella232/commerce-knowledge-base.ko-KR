---
title: 'ACSD-54319: 제품 가격이 *에서 0을 표시함[!UICONTROL Products in Carts]* 보고서'
description: ACSD-54319 패치를 적용하여 제품 가격이 *에서 0으로 표시되는 Adobe Commerce 문제를 해결합니다.[!UICONTROL Products in Carts]* 보고서
feature: Reporting, Products
role: Admin, Developer
exl-id: f53b3ed3-d5d5-461c-bba2-4f9f3f038580
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-54319: 제품 가격이 0으로 표시됨 *[!UICONTROL Products in Carts]* 보고서

ACSD-54319 패치는에서 제품 가격이 0으로 표시되는 문제를 해결합니다. *[!UICONTROL Products in Carts]* 보고서. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40이 설치되었습니다. 패치 ID는 ACSD-54319입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 가격이 0으로 표시됩니다. *[!UICONTROL Products in Carts]* 보고서.

<u>재현 단계</u>:

1. 설정 **[!UICONTROL Catalog Price Scope]** 끝 **[!UICONTROL Website]** 출처: **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**.
1. 에서 두 번째 웹 사이트 만들기 **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. 에서 제품 만들기 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. 이 제품을 두 번째 웹 사이트에만 할당합니다.
1. 두 번째 웹 사이트에서 제품을 장바구니에 추가합니다.
1. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]** 그리드.
1. 다음 확인: *[!UICONTROL Price]* 열 위치 *[!UICONTROL Products In Carts]* 그리드.

<u>예상 결과</u>:

제품 가격이 0이 아닙니다. *[!UICONTROL Products in Carts]* 보고서 그리드.

<u>실제 결과</u>:

제품 가격이 0 *[!UICONTROL Products in Carts]* 보고서 그리드.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
