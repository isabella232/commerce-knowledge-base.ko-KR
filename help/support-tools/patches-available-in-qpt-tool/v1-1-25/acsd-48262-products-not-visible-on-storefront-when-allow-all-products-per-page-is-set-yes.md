---
title: 'ACSD-48262: 다음과 같은 경우 제품이 상점 앞에 표시되지 않음 [!UICONTROL Allow All Products Per Page] 은(는) 설정되어 있습니다. [!UICONTROL Yes]'
description: ACSD-48262 패치를 적용하여 다음과 같은 경우 제품이 상점 앞에 표시되지 않는 Adobe Commerce 문제를 해결합니다. [!UICONTROL Allow All Products Per Page] 설정이 로 설정되어 있습니다. [!UICONTROL Yes].
exl-id: 327cad03-441d-4adb-8a10-802f06d3fcd1
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-48262: 다음과 같은 경우 제품이 상점 앞에 표시되지 않음 [!UICONTROL Allow All Products Per Page] 은(는) 설정되어 있습니다. *[!UICONTROL Yes]*

ACSD-48262 패치는 다음과 같은 경우 제품이 상점 앞에 표시되지 않는 문제를 해결합니다. [!UICONTROL Allow All Products Per Page] 설정이 로 설정되어 있습니다. *[!UICONTROL Yes]*. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25가 설치되어 있습니다. 패치 ID는 ACSD-48262입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

ACSD-48262 패치는 다음과 같은 경우 제품이 상점 앞에 표시되지 않는 문제를 해결합니다. [!UICONTROL Allow All Products Per Page] 설정이 로 설정되어 있습니다. *[!UICONTROL Yes]*.

<u>재현 단계</u>:

1. 테스트 카테고리를 만듭니다.
1. 테스트 범주에서 테스트 제품을 만듭니다.
1. 제품을 탐색하여 상점 첫 화면에서 카테고리 페이지를 테스트하고 제품이 보이는지 확인하십시오.
1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** 및 설정 [!UICONTROL Allow All Products Per Page] 설정 *[!UICONTROL Yes]*.
1. 캐시를 지웁니다.
1. 상점 첫 화면에서 카테고리 페이지를 확인하십시오.

<u>예상 결과</u>:

제품이 표시됩니다.

<u>실제 결과</u>:

제품이 보이지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.


## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
