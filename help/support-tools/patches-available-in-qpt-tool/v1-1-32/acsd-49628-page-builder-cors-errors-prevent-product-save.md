---
title: 'ACSD-49628: [!DNL Page Builder] CORS 오류로 인해 제품 저장 방지'
description: ACSD-49628 패치를 적용하여 다음과 같은 Adobe Commerce 문제를 해결합니다. [!DNL Page Builder] CORS 오류로 인해 제품이 저장되지 않습니다.
exl-id: c6e2f0b3-aea0-4caf-8b69-9644b38c909c
feature: Categories, Page Builder, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49628: [!DNL Page Builder] CORS 오류로 인해 제품 저장 방지

ACSD-49628 패치는 다음과 같은 문제를 해결합니다. [!DNL Page Builder] CORS 오류로 인해 관리자가 제품을 저장할 수 없습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.32가 설치되어 있습니다. 패치 ID는 ACSD-49628입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Page Builder] CORS 오류로 인해 제품이 저장되지 않습니다.

<u>재현 단계</u>:

1. 관리자로 로그인합니다.
1. 다음 권한을 사용하여 사용자 역할을 만듭니다.

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. 추가 안 함 *[!UICONTROL Content]* 사용 권한.
1. 다른 관리 사용자를 만들고 위에서 만든 역할을 이 사용자에게 할당합니다.
1. 제품을 만들고 로그아웃합니다.
1. 두 번째 관리자로 로그인합니다.
1. 제품을 편집하고 저장해 보십시오.

<u>예상 결과</u>:

두 번째 관리자는 제품을 저장할 수 있지만 **[!UICONTROL Edit with Page Builder]** 단추가 관리자 없이 표시되지 않음 *[!UICONTROL Content]* 사용 권한.

<u>실제 결과</u>:

두 번째 관리자는 여러 명으로 인해 제품을 저장할 수 없습니다. [!DNL Page Builder] 오류.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
