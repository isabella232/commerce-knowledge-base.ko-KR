---
title: 'ACSD-53636: 정가가 다음에 표시되지 않음 [!UICONTROL Product Listing] 페이지'
description: ACSD-53636 패치를 적용하여 *에 일반 가격이 표시되지 않는 Adobe Commerce 문제를 수정합니다.[!UICONTROL Product Listing]* 특별 가격이 적용된 하위 제품이 있는 구성 가능한 제품 페이지입니다.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: 97b4eb64-92d1-4db1-8e5b-915b16115663
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-53636: 정가가 다음에 표시되지 않음 *[!UICONTROL Product Listing]* 페이지

ACSD-53636 패치는에 일반 가격이 표시되지 않는 문제를 해결합니다 *[!UICONTROL Product Listing]* 특별 가격으로 하위 제품이 있는 구성 가능한 제품 페이지. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43이 설치되었습니다. 패치 ID는 ACSD-53636입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

정가는 다음에 표시되지 않습니다 *[!UICONTROL Product Listing]* 특별 가격으로 하위 제품이 있는 구성 가능한 제품 페이지.

<u>재현 단계</u>:

1. 관리자에 로그인하고 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Catalog]**&#x200B;을 클릭하고, 구성 가능한 제품을 만들거나 엽니다.
2. 하위 제품을 열고 하위 제품 전체 또는 중 하나에 특별 가격을 추가하고 제품을 저장합니다.
3. 프론트엔드로 이동하여 **[!UICONTROL Product Detail]** 구성 가능한 제품의 페이지입니다. 특별 가격이 있는 하위 제품의 견본에 *[!UICONTROL Regular price]* 취소했습니다(예상됨).
4. 프론트엔드로 이동하여 **[!UICONTROL Product Listing]** 특별 가격으로 구성 가능한 제품의 페이지입니다. 구성 가능한 제품 견본 변경 사항은 다음과 달리 일반 가격을 표시하지 않습니다. *[!UICONTROL Product Detail Page]* 및 기타 간단한 제품

<u>예상 결과</u>:

다음에서 *[!UICONTROL Product Listing]* 페이지에서 구성 가능한 제품은 하위 제품에 대한 일반 가격을 표시합니다.

<u>실제 결과</u>:

다음에서 *[!UICONTROL Product Listing]* 페이지에서 구성 가능한 제품은 하위 제품에 대한 일반 가격을 표시하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
