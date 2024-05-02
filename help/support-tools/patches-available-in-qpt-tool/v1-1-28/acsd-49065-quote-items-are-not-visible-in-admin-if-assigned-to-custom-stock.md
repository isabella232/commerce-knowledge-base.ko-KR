---
title: 'ACSD-49065: 관리자에 견적 항목이 표시되지 않음'
description: ACSD-49065 패치를 적용하여 견적 항목이 사용자 지정 재고에만 할당된 경우 관리자에 표시되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 3a5ceb4c-4c94-4938-98d9-9171f2633056
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-49065: 관리자에 견적 항목이 표시되지 않음

ACSD-49065 패치는 견적 항목이 사용자 지정 재고에만 할당된 경우 관리자에 표시되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28이 설치되었습니다. 패치 ID는 ACSD-49065입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

견적 항목이 사용자 지정 주식에만 할당된 경우 관리자에 표시되지 않습니다.

사전 요구 사항:

**[!UICONTROL B2B]** 및 **[!UICONTROL Inventory]** 모듈을 설치해야 합니다.

<u>재현 단계</u>:

1. 사용 **[!UICONTROL Company]** 및 **[!UICONTROL B2B Quote]** 아래에 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. 보조 만들기 **[!UICONTROL Inventory Source]** 보조 사용자에게 할당 **[!UICONTROL Inventory Stock]**.
1. 보조(기본값이 아님)만 할당하여 새 제품 만들기 **[!UICONTROL Inventory Source]**.
1. 상점으로 이동하여 새 회사 계정을 만듭니다. 다음으로 로그인 **[!UICONTROL Company Admin]**&#x200B;을 클릭하고 만든 제품을 장바구니에 추가합니다.
1. 장바구니로 이동하고 *[!UICONTROL Request a Quote]*.
1. 관리자로 이동하여 다음 위치에서 요청한 견적을 봅니다. **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>예상 결과</u>:

항목은 제품을 다시 저장하지 않고 새 제품으로 생성된 새 견적에 표시됩니다.

<u>실제 결과</u>:

다음 *[!UICONTROL Items Quoted]* 섹션이 비어 있습니다. 새로 만든 제품을 다시 저장하면 항목이 나타납니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
