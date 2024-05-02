---
title: '''ACSD-53176: ''is one of'' 조건이 있는 제품 규칙이 일치하지 않음'''
description: ACSD-53176 패치를 적용하여 관련 제품 규칙 'is one of' 조건이 'Products to Match'에 대해 제대로 작동하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Marketing Tools
role: Admin
exl-id: 91f05f5b-6a5e-4b93-9dfb-88cbeccb6c9e
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-53176: 제품 규칙 `is one of` 조건이 일치하지 않음

ACSD-53176 패치는 관련 제품 규칙에서 발생하는 문제를 해결합니다 `is one of` 에 대한 조건이 올바르게 작동하지 않음 **일치하는 제품**. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.36이 설치되었습니다. 패치 ID는 ACSD-53176입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관련 제품 규칙 `is one of` 에 대한 조건이 올바르게 작동하지 않음 **일치하는 제품**.

<u>재현 단계</u>:

1. 3~4개의 제품을 만듭니다.
1. 새 관련 제품 규칙을 만듭니다.

   둘 이상의 제품과 일치하도록 규칙을 설정합니다.
   * `SKU is one of "S1,S2".`

   두 개 이상의 항목을 표시하는 규칙을 설정합니다.
   * `Product SKU is one of constant value "S2,S3".`

1. 상점에서 S1 제품을 엽니다.

<u>예상 결과</u>:

관련 제품 &quot;S2&quot;와 &quot;S3&quot;은 제품 페이지 &quot;S1&quot;과 &quot;S2&quot;에 모두 표시됩니다.

<u>실제 결과</u>:

관련 제품이 제품 페이지에 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
