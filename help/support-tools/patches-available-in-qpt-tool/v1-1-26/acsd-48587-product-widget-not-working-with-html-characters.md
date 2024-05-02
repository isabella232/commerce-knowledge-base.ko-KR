---
title: 'ACSD-48587: 제품 위젯이 HTML 문자가 포함된 SKU에서 작동하지 않음'
description: ACSD-48587 패치를 적용하여 제품 위젯 일치 규칙에 특수 문자 HTML이 일치하는 제품을 표시하지 못하는 Adobe Commerce 문제를 해결합니다.
exl-id: 9f8f436c-f3ef-4510-a941-12f701e7524e
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48587: 제품 위젯이 HTML 문자가 포함된 SKU에서 작동하지 않음

ACSD-48587 패치는 제품 위젯 일치 규칙에 특수 문자 HTML이 일치하는 제품을 표시하지 못하는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26이 설치되었습니다. 패치 ID는 ACSD-48587입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 위젯이 이 포함된 SKU에서 작동하지 않습니다. *&quot;&amp;&quot;* 기호.

<u>재현 단계</u>:

1. 다음을 포함하는 제품 만들기 *&quot;&amp;&quot;* (예: s000&amp;01).
1. 에서 CMS 페이지의 콘텐츠를 편집합니다. *페이지 빌더*.
1. 제품 위젯을 추가합니다.
1. 위젯 편집 및 설정 **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. 다음을 포함하는 SKU를 입력합니다. *&quot;&amp;&quot;* 제품 SKU 필드에서 참조할 수 있습니다.
1. 콘텐츠 및 CMS 페이지를 저장합니다.
1. 다음 확인: *CMS 페이지* 에 대한 콘텐츠 *페이지 빌더 미리보기* 그리고 제품 상점.

<u>예상 결과</u>:

이 있는 제품 *&quot;&amp;&quot;* sku의 는 페이지 빌더 미리보기 및 상점에 표시됩니다.

<u>실제 결과</u>:

이 있는 제품 *&quot;&amp;&quot;* 의 SKU는 페이지 빌더 미리 보기에 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
