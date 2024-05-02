---
title: 'ACSD-45168: url_key 특성이 재정의된 제품에 대해 SEO 친화적 URL이 생성되지 않음'
description: ACSD-45168 패치를 적용하여 스토어-보기 수준에서 url_key 특성이 재정의된 제품에 대해 SEO 친화적 URL이 생성되지 않는 Adobe Commerce 문제를 수정합니다.
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168: url_key 특성이 재정의된 제품에 대해 SEO에 친숙한 URL이 생성되지 않음

ACSD-45168 패치는 스토어-보기 수준에서 url_key 특성이 재정의된 제품에 대해 SEO에 친숙한 URL이 생성되지 않는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되었습니다. 패치 ID는 ACSD-45168입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

스토어-뷰 수준에서 url_key 특성이 재정의된 제품에 대해서는 SEO에 친숙한 URL이 생성되지 않습니다.

<u>재현 단계</u>:

1. 로 이동하여 구성을 다음과 같이 설정합니다. **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *예*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *예*
1. 구성 캐시를 정리합니다.
1. 다음 두 가지 카테고리를 만듭니다. [!UICONTROL Category 1] 및 [!UICONTROL Category 2].
1. 다음 두 가지 제품을 만듭니다. [!UICONTROL Product 1] 위치: [!UICONTROL Category 1], [!UICONTROL Product 2] 위치: [!UICONTROL Category 1].
1. 범위를 다음으로 변경 [!UICONTROL Default Store View] 대상 [!UICONTROL Product 1].
1. 선택적 URL 선택 취소 [!UICONTROL Key] 위치: [!UICONTROL Search Engine Optimization].
1. 제품을 저장합니다.
1. 다음으로 다시 전환 [!UICONTROL All Store Views].
1. 추가 [!UICONTROL Product 1] 끝 [!UICONTROL Category 2], 및 추가 [!UICONTROL Product 2] 끝 [!UICONTROL Category 2].
1. 다음 확인: [!UICONTROL url_rewrite] 표 또는 [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>예상 결과</u>:

에 대한 SEO 기반 URL [!UICONTROL Category 2] 다음에 대해 생성됨: [!UICONTROL Product 1].

<u>실제 결과</u>:

에 대한 SEO 기반 URL [!UICONTROL Category 2] 이(가)에 대해 누락되었습니다. [!UICONTROL Product 1] 스토어 보기 범위에 대해 URL 키 속성을 덮어썼기 때문입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
