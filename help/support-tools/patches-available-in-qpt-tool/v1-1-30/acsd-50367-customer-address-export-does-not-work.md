---
title: 'ACSD-50367: 고객 주소 내보내기가 다중 선택 특성과 함께 작동하지 않음'
description: 값이 없는 다중 선택 **`고객 주소`** 속성이 생성될 때 고객 주소 내보내기가 작동하지 않는 Adobe Commerce 문제를 해결하려면 ACSD-50367 패치를 적용합니다.
exl-id: 688831d4-b49e-48fa-b4db-1328cda09a2b
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-50367: 고객 주소 내보내기가 작동하지 않음

ACSD-50367 패치는 다중 선택 시 고객 주소 내보내기가 작동하지 않는 문제를 해결합니다 **`Customer Address`** 값이 없는 속성이 만들어집니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되었습니다. 패치 ID는 ACSD-50367입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다중 선택 시 고객 주소 내보내기가 작동하지 않음 **`Customer Address`** 값이 없는 속성이 만들어집니다.

<u>전제 조건</u>:

주소를 사용하여 고객을 만듭니다.

<u>재현 단계</u>:

1. 다중 선택 만들기 **`Customer Address`** 의 속성 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]**, 및 선택 **`Customer Address`** 엔티티 유형.
1. 고객 주소를 내보냅니다. 내보내는 항목이 없습니다.
1. 다중 선택 삭제 **`Customer Address`** 속성을 지정하고 고객 주소를 다시 내보냅니다. 이번에는 주소의 CSV 파일이 생성됩니다.

<u>예상 결과</u>:

다중 선택 시 고객 주소를 CSV 파일로 내보낼 수 있습니다 **`Customer Address`** 속성이 작성됩니다.

<u>실제 결과</u>:

다중 선택 시 고객 주소를 CSV 파일로 내보낼 수 없습니다 **`Customer Address`** 속성이 작성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
