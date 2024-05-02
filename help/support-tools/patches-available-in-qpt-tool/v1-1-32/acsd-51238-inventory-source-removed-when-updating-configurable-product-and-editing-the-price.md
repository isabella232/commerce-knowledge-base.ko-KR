---
title: 'ACSD-51238: 구성 가능한 제품을 업데이트하고 가격을 편집할 때 재고 소스가 제거됨'
description: ACSD-51238 패치를 적용하여 구성 가능한 제품을 업데이트하고 가격을 편집할 때 인벤토리 소스가 제거되는 Adobe Commerce 문제를 해결합니다.
exl-id: ab2f60fd-5da3-45f7-a489-6f4f9d34e1f1
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51238: 구성 가능한 제품을 업데이트하고 가격을 편집할 때 재고 출처가 제거됩니다.

ACSD-51238 패치는 구성 가능한 제품을 업데이트하고 가격을 편집할 때 인벤토리 소스가 제거되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.32가 설치되어 있습니다. 패치 ID는 ACSD-51238입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품을 업데이트하고 가격을 편집할 때 재고 출처가 제거됩니다.

<u>재현 단계</u>:

1. 설치 **[!DNL Adobe Commerce]** 포함 **[!DNL Inventory module]**
1. 로 이동 **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** 및 만들기 *두 가지 소스* 및 *두 개의 주식*.
1. 만들기 **[!UICONTROL configurable product]** 할당 대상: **[!UICONTROL default sources]** 또는 **[!UICONTROL newly created sources]**.
1. 을(를) 클릭합니다 **[!UICONTROL next button]** 및 *저장* 제품.
1. 이제 동일한 항목 편집 **[!UICONTROL Configurable Product]** 및 클릭 **[!UICONTROL Edit Configuration]** 의 내부 **[!UICONTROL Configuration tab]**.
1. 위치 `Step 3: Bulk Images,Price and Quantity`, 변경 `price` 및 나가기 `Quantity` 및 `Images` 끝 `Skip quantity at this time` 및 `Skip image uploading at this time` 각각.
1. 클릭 **[!UICONTROL next button]** 제품을 생성합니다.

<u>예상 결과</u>

내의 소스당 수량 **[!UICONTROL Configuration tab]** 비워둘 수 없습니다.

<u>실제 결과</u>

내의 소스당 수량 **[!UICONTROL Configuration tab]** 은(는) 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 다음에서 [!DNL Quality Patches Tool] 가이드.
