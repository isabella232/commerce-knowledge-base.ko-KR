---
title: '''ACSD-48234: 다음 경우에 카탈로그 검색 결과가 잘못된 범주 항목 수입니다. [!UICONTROL Display Out of Stock Products] 활성화됨'
description: ACSD-48234 패치를 적용하여 다음과 같은 경우 카탈로그 검색 결과에 잘못된 범주 항목 수가 표시되는 Adobe Commerce 문제를 해결합니다. [!UICONTROL Display Out of Stock Products] 옵션이 활성화되어 있습니다.
exl-id: 8e70fe73-d550-4e11-b25e-84955e136d12
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48234: 카탈로그 검색 결과에 잘못된 범주 항목 수가 표시됨 **[!UICONTROL Display Out of Stock Products]** 활성화됨

ACSD-48234 패치는 다음을 실행할 때 카탈로그 검색 결과에 잘못된 범주 항목 수가 표시되는 문제를 해결합니다. **[!UICONTROL Display Out of Stock Products]** 옵션이 활성화되어 있습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25가 설치되어 있습니다. 패치 ID는 ACSD-48234입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.


## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**
* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음을 실행할 때 카탈로그 검색 결과에 잘못된 범주 항목 카운트가 표시됩니다. **[!UICONTROL Display Out of Stock Products]** 옵션이 활성화되어 있습니다.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** 및 열기 **[!UICONTROL color]** 특성.
1. 주황색과 녹색과 같은 두 가지 옵션을 추가합니다. 속성을 저장합니다.
1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** 및 추가 **[!UICONTROL color]** 속성 **[!UICONTROL Default]** 속성 집합입니다.
1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** 및 설정 **[!UICONTROL Display Out of Stock Products]** 끝 _예_.
1. 범주 &quot;cat1&quot;을 만듭니다.
1. 다음 두 가지 제품을 만듭니다.
   1. 이름: prod1, 색상: 주황색, 범주: cat1.
   1. 이름: prod2, 색상: 녹색, 범주: cat1.
1. 상점 앞에서 cat1 카테고리를 엽니다.
1. 레이어 탐색에서 주황색 색상을 선택합니다.

<u>예상 결과</u>:

prod1 제품만 표시됩니다.

<u>실제 결과</u>:

prod1 및 prod2 제품이 모두 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
