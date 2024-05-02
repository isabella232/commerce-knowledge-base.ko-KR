---
title: '''ACSD-54776: 선택 안 함 [!UICONTROL Use Default Value] 및 기본값이 아닌 제품 필드 값은 두 번째 웹 사이트, 스토어 및 스토어 보기에 대해 저장되지 않습니다.'
description: ACSD-54776 패치를 적용하여 이 선택되지 않은 Adobe Commerce 문제를 해결합니다. [!UICONTROL Use Default Value] 및 기본값이 아닌 제품 필드 값은 두 번째 웹 사이트, 스토어 및 스토어 보기에 대해 저장되지 않습니다.
feature: Products
role: Admin, Developer
exl-id: 5bdad804-8d7b-48b4-ba3b-c2d5387ef55e
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-54776: 선택 취소됨 *[!UICONTROL Use Default Value]* 및 기본값이 아닌 제품 필드 값은 저장되지 않습니다

>[!NOTE]
>
>이 패치는 [ACSD-51984](/help/support-tools/patches-available-in-qpt-tool/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) qpt 1.1.35에서 발표된 패치.

ACSD-54776 패치는 선택 취소되는 문제를 해결합니다 **[!UICONTROL Use Default Value]** 및 기본값이 아닌 제품 필드 값은 두 번째 웹 사이트, 스토어 및 스토어 보기에 대해 저장되지 않습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39가 설치되었습니다. 패치 ID는 ACSD-54776입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p4, 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

선택되지 않음 *[!UICONTROL Use Default Value]* 및 기본값이 아닌 제품 필드 값은 두 번째 웹 사이트, 스토어 및 스토어 보기에 대해 저장되지 않습니다.

<u>재현 단계</u>:

1. 백엔드로 이동하여 다음 위치로 이동합니다. **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** 새 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. 다음으로 이동 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;를 클릭하고 간단한 제품을 만들어 저장한 다음, **[!UICONTROL Product in Websites]**.
1. 2단계에서 새로 만든 스토어 보기로 범위를 변경합니다.
1. 다음으로 이동 **[!UICONTROL Search Engine Optimization]** 및 선택 취소 **[!UICONTROL Use Default Value]** 확인란 [!UICONTROL Meta Title], [!UICONTROL Meta Keywords], 및 [!UICONTROL Meta Description].
1. 필드에서 텍스트를 정리합니다. *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* 및 *[!UICONTROL Meta Description]*, 및 클릭 **[!UICONTROL Save]**.
1. 다음으로 이동 **[!UICONTROL Search Engine Optimization]** 다시.

<u>예상 결과</u>

필드 및 확인란의 값이 저장됩니다.

<u>실제 결과</u>

필드 및 확인란의 값이 저장되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 다음에서 [!DNL Quality Patches Tool] 가이드.
