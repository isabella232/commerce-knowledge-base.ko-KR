---
title: 'ACSD-51497: 드롭다운 유형의 사용자 지정 특성별로 카탈로그 페이지를 정렬할 수 없음'
description: ACSD-51497 패치를 적용하여 고객이 드롭다운 유형의 사용자 지정 특성별로 카탈로그 페이지를 정렬할 수 없는 Adobe Commerce 문제를 수정합니다.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: 60a4f375-9b9a-4026-9dc7-d9f847a75656
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-51497: 유형의 사용자 지정 특성별로 카탈로그 페이지를 정렬할 수 없음 *드롭다운*

ACSD-51497 패치는 고객이 유형의 사용자 지정 특성으로 카탈로그 페이지를 정렬할 수 없는 문제를 수정합니다 *드롭다운*. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33이 설치되었습니다. 패치 ID는 ACSD-51497입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객이 유형의 사용자 지정 특성으로 카탈로그 페이지를 정렬할 수 없습니다. *드롭다운*.

<u>재현 단계</u>

1. 6가지 정도의 간단한 제품을 만들어 하나의 카테고리에 할당합니다.
1. 목록 페이지에서 정렬 옵션으로 추가하려면 제품 속성을 만듭니다.

   * 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * 다음에서 **[!UICONTROL Properties]** 탭에서 다음을 설정합니다.

      * *[!UICONTROL Default Label]* = *테스트*
      * *[!UICONTROL Catalog Input Type]* 스토어 소유자용 = *드롭다운*
      * *[!UICONTROL Options]*:

         * *첫 번째*
         * *초*
         * *세 번째*
         * *네 번째*

   * 다음에서 **[!UICONTROL Storefront Properties]** 탭에서 다음을 설정합니다.

      * *[!UICONTROL Used for sorting in product listing]* = *예*
      * 다른 모든 옵션은 다음과 같이 둡니다. *기본값*.

1. 할당 *테스트* 속성 *기본값* 속성 설정 위치 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. 다음을 갖도록 제품 구성 *테스트* 속성 값.

   * SKU: s00001, 테스트: 네 번째
   * SKU: s00002, 테스트: 세 번째
   * SKU: s00003, 테스트: 초
   * SKU: s00004, 테스트: 첫 번째
   * SKU: s00005, 테스트: 네 번째
   * SKU: s00006, 테스트: 세 번째

1. 캐시를 다시 인덱싱하고 지웁니다.
1. 가게 앞에 있는 카테고리로 가세요.
1. 정렬 기준: *테스트* 특성.

<u>예상 결과</u>:

제품은 다음을 기준으로 정렬됩니다. *테스트* 특성.

<u>실제 결과</u>:

제품이 다음 기준으로 정렬되지 않음: *테스트* 특성.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
