---
title: 'ACSD-49706: 값을 선택하지 않은 경우 시각적 견본 속성에 대해 저장된 기본값'
description: 값을 선택하지 않은 경우 시각적 견본 속성에 대해 기본값이 저장되는 Adobe Commerce 문제를 해결하려면 ACSD-49706 패치를 적용합니다.
exl-id: fe6071df-f2a4-443a-acfa-67f3d253c5e4
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-49706: 값을 선택하지 않은 경우 시각적 견본 속성에 대해 저장된 기본값

ACSD-49706 패치는 값을 선택하지 않은 경우 시각적 견본 속성에 대해 기본값이 저장되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29가 설치되었습니다. 패치 ID는 ACSD-49706입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

값을 선택하지 않으면 시각적 견본 속성에 대해 기본값이 저장됩니다.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. 클릭 **[!UICONTROL Add New Attribute]**.
1. 필드를 채웁니다.

   * 예를 들어 입력 유형을 선택합니다 *[!UICONTROL Visual Swatch]*, 여러 옵션 추가(예: *빨강*, *녹색*). 이러한 옵션 중 하나를 기본값으로 선택해야 합니다.
   * 클릭 **[!UICONTROL Save Attribute]**.

1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. 편집 *[!UICONTROL Default]* 속성 집합입니다.
1. 이동 *[!UICONTROL New Attribute]* 열에서 *[!UICONTROL Unassigned Attributes]* (으)로 *[!UICONTROL Product Details]* 가운데 열에 있는 폴더입니다.

   * 클릭 **[!UICONTROL Save]**.

1. 를 사용하여 새 제품 만들기 *[!UICONTROL Default]* 속성 집합입니다.

   * 나가기 *[!UICONTROL New Attribute]* 비우고 저장하십시오.

1. 저장되면 값이 *[!UICONTROL New Attribute]*.

<u>예상 결과</u>:

할당된 값 없음 *[!UICONTROL New Attribute]* 기본적으로.

<u>실제 결과</u>:

제품 저장 시 속성에 기본값이 적용됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
