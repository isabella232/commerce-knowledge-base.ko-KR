---
title: 'ACSD-52095: CSV를 내보내는 동안 재고 값 관리가 잘못됨'
description: ACSD-52095 패치를 적용하여 CSV를 내보내는 동안 제품 관리 스톡 값이 잘못된 Adobe Commerce 문제를 해결합니다.
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095: [!UICONTROL Manage Stock] csv를 내보내는 중 값이 잘못되었습니다.

ACSD-52095 패치는 제품에서 발생하는 문제를 해결합니다 `manage_stock` csv를 내보내는 동안 값이 잘못되었습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있습니다. 패치 ID는 ACSD-52095입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음 `manage_stock` 제품 내보내기 후 CSV 파일에서 값이 0으로 잘못 설정되었습니다.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** 및 설정 **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. 새 제품을 만들고 저장합니다.
1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. 선택 *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* 제품을 내보냅니다.
1. 생성된 CSV 파일 확인: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. 다시 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**, 및 설정  **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. 다음으로 이동 **시스템** > **내보내기**.
선택 *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. 생성된 CSV 파일 확인: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. 관리자에서 제품을 열고 **[!UICONTROL Advanced Inventory]** 및 확인 **[!UICONTROL Manage Stock]** 값.

<u>예상 결과</u>

다음 **[!UICONTROL Manage Stock]** 값: *1* 제품에 대해 활성화된 경우.

<u>실제 결과</u>

다음 **[!UICONTROL Manage Stock]** 값: *0* 제품에 대해 활성화된 경우.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 다음에서 [!DNL Quality Patches Tool] 가이드.
