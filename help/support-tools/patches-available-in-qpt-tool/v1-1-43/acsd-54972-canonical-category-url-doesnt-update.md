---
title: 'ACSD-54972: 표준 범주 URL이 업데이트되지 않음'
description: ACSD-54972 패치를 적용하여 카테고리 URL을 변경한 후 표준 카테고리 URL이 업데이트되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management, Products, Categories
role: Admin, Developer
exl-id: 2d78f5f6-d485-45a4-a40d-9a0ddd124f82
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-54972: 범주 URL을 변경한 후 표준 범주 URL이 업데이트되지 않음

ACSD-54972 패치는 범주 URL을 변경한 후 표준 범주 URL이 업데이트되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43이 설치되었습니다. 패치 ID는 ACSD-54972입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

표준 범주 URL은 범주 URL을 변경한 후에는 업데이트되지 않습니다.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**.

   * 설정 *[!UICONTROL Use Canonical Link Meta Tag for Categories]*: *예*

2. 카테고리 만들기(예: *이름*: *범주 01*, *URL 키*: *category-01*).
3. 업데이트 *URL 키* 을 유지하면서 원래 값과 다른 값으로 **[!UICONTROL Create Permanent Redirect for old URL]** 확인란이 똑딱거립니다.
4. 캐시를 정리합니다.
5. 로 이동 *[!UICONTROL Category Page]* 앞쪽에 있습니다.
6. 페이지 소스를 확인하고 *표준-* 태그에 가깝게 배치하십시오.

<u>예상 결과</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u>실제 결과</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
