---
title: 'ACSD-52786: 카탈로그 규칙 *[!UICONTROL SKU is]* SKU로 시작하는 모든 제품에 적용됩니다.'
description: ACSD-52786 패치를 적용하여 카탈로그 규칙 조건*이 있는 Adobe Commerce 문제를 해결합니다.[!UICONTROL SKU is]* 해당 SKU로 시작하는 모든 제품에 적용됩니다.
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786: 카탈로그 규칙 &quot;*[!UICONTROL SKU is]*&quot;는 SKU로 시작하는 모든 제품에 적용됩니다.

ACSD-52786 패치는 카탈로그 규칙 조건 문제를 해결합니다 *[!UICONTROL SKU is]* 은 제공된 SKU로 시작하는 모든 제품에 적용됩니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있습니다. 패치 ID는 ACSD-52786입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

카탈로그 규칙 조건 *[!UICONTROL SKU is]* 은 제공된 SKU로 시작하는 모든 제품에 적용됩니다.

<u>재현 단계</u>:

1. SKU &quot;24&quot;와 SKU &quot;24-MB01&quot;의 두 제품을 만듭니다.
1. 다음으로 이동 **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. 다음 조건을 적용합니다.
   * *[!UICONTROL If **&#x200B;모두&#x200B;**이 중 다음과 같은 조건이 있습니다**&#x200B;참&#x200B;**]*: *[!UICONTROL SKU is 24]*
1. 액션에서 할인 금액을 설정합니다.
1. 클릭 **[!UICONTROL Save and Apply]**.
1. 캐시를 플러시합니다.
1. 가게 앞에 가셔서 24MB01의 가격을 확인해 보세요

<u>예상 결과</u>:

카탈로그 규칙은 SKU가 24와 같은 단일 제품에만 적용됩니다.

<u>실제 결과</u>:

카탈로그 규칙 조건 *[!UICONTROL SKU is]* 은 제공된 SKU로 시작하는 모든 제품에 적용됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
