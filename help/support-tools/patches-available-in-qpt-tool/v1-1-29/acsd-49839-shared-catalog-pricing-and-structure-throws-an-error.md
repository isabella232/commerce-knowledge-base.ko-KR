---
title: 'ACSD-49839: 공유 카탈로그 가격 및 구조에서 오류가 발생합니다.'
description: ACSD-49839 패치를 적용하여 제품이 SKU에서 작은따옴표나 큰따옴표를 가질 때 공유 카탈로그 가격 및 구조로 인해 관리자에게 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
exl-id: 4c477ae8-602b-452e-83f0-b72a29547ef9
feature: Admin Workspace, Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49839: 공유 카탈로그 가격 및 구조에서 오류가 발생합니다.

ACSD-49839 패치는 SKU에서 제품에 작은따옴표나 큰따옴표가 있을 때 공유 카탈로그 가격 및 구조에서 관리자에게 오류가 발생하는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29가 설치되었습니다. 패치 ID는 ACSD-49839입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

SKU에서 제품에 작은 따옴표나 큰 따옴표가 있을 때 공유 카탈로그 가격 및 구조에서 관리자에게 오류가 발생합니다.

<u>재현 단계</u>:

1. 제품 SKU 중 일부를 다음과 같은 특수 문자(예: 큰따옴표)로 설정합니다.
   *[제품&quot;12, 제품&quot;14, 제품&quot;15]*.
1. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Add Shared Catalog]** (예:*[공유 카탈로그 테스트]*).
1. 모두 할당 **[!UICONTROL Products and Categories]** > **[!UICONTROL Generate Catalog]** > **[!UICONTROL Save]**.
1. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Test Shared Catalog]** > **[!UICONTROL Action]** > **[!UICONTROL Set Pricing and Structure]**.
1. 표시 *[!UICONTROL Root Catalog]* 모든 카테고리와 제품을 선택합니다.
1. 네트워크 패널에서 AJAX 요청을 확인합니다.

<u>예상 결과</u>:

SKU에서 제품에 작은 따옴표나 큰 따옴표가 있을 때 공유 카탈로그 가격 및 구조에서 관리자에 오류가 발생하지 않습니다.

<u>실제 결과</u>:

SKU에서 제품에 작은 따옴표나 큰 따옴표가 있을 때 공유 카탈로그 가격 및 구조에서 관리자에 오류가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
