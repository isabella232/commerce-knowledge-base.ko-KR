---
title: 'ACSD-50813: 관리자가 슬래시가 포함된 번들 제품을 추가할 수 없음'
description: ACSD-50813 패치를 적용하여 관리자가 *SKU별 제품 추가* 기능이 있는 SKU의 슬래시 표시(`/`)가 포함된 번들 제품을 관리자 주문에 추가할 수 없는 Adobe Commerce 성능 문제를 해결합니다.
exl-id: 80dfe877-9dfd-44a9-9bf0-37e929642fc0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-50813: 관리자가 슬래시가 포함된 번들 제품을 추가할 수 없음

ACSD-50813 패치는 관리자가 슬래시 표시( )가 포함된 번들 제품을 추가할 수 없는 문제를 해결합니다.`/`)를 사용하여 SKU에서 *[!UICONTROL Add Products by SKU]* 관리 순서에 대한 기능입니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.34가 설치되어 있습니다. 패치 ID는 ACSD-50813입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자는 슬래시 표시( )가 포함된 번들 제품을 추가할 수 없습니다.`/`)를 사용하여 SKU에서 *[!UICONTROL Add Products by SKU]* 관리 순서에 대한 기능입니다.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. 간단한 제품을 만듭니다.
1. 새 번들 제품을 만듭니다.
1. 슬래시 표시 추가(`/`) SKU 중간(예: *Bu/ndle*).
1. 와 함께 번들 옵션 추가 **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*.
1. 하나 이상의 간단한 제품을 옵션에 할당합니다.
1. 다음으로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;을 클릭하고 새 주문을 만듭니다.
1. 클릭 **[!UICONTROL Add Products by SKU]**.
1. SKU를 입력하고 을(를) 클릭합니다. **[!UICONTROL Add to Order]**.
1. 브라우저 콘솔을 엽니다.
1. 클릭 **[!UICONTROL Configure]**.

<u>예상 결과</u>:

오류가 없습니다.

<u>실제 결과</u>:

콘솔의 JS 오류:

*확인할 수 없는 오류: 구문 오류, 인식할 수 없는 표현식: div[id=sku_bu/ndle]*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
