---
title: 'ACSD-49286: 여러 제품 위젯이 있는 경우 제품이 장바구니에 두 번 추가됨'
description: ACSD-49286 패치를 적용하여 페이지에 여러 제품 위젯이 있을 때 제품이 장바구니에 두 번 추가되는 Adobe Commerce 문제를 수정합니다.
exl-id: b1764943-945d-4ef9-9bbe-3f3c8383b5b1
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49286: 여러 제품 위젯이 있는 경우 장바구니에 제품이 두 번 추가되었습니다.

ACSD-49286 패치는 페이지에 여러 제품 위젯이 있을 때 제품이 장바구니에 두 번 추가되는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28이 설치되었습니다. 패치 ID는 ACSD-49286입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

페이지에 여러 제품 위젯이 있는 경우 제품이 장바구니에 두 번 추가됩니다.

<u>재현 단계</u>:

1. 관리자에 로그인하고 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. 콘텐츠 섹션에서 을(를) 클릭합니다. **[!UICONTROL Edit]** 사용 [!DNL Page Builder].
1. 두 행 요소를 추가할 위치 **[!UICONTROL Content]**.
1. 두 행 요소에 제품을 추가합니다.
1. 첫 번째 행에서 제품 모양을 로 설정합니다. [!UICONTROL Product Grid] 표시할 카테고리를 선택합니다.
1. 두 번째 행에서 제품 모양을 로 설정합니다. [!UICONTROL Product Carousel] 표시할 다른 범주를 선택합니다.
1. 상점 앞으로 가세요 **[!UICONTROL Home Page]**&#x200B;제품 그리드에서 제품 하나를 추가합니다.
1. 에서 다른 제품 추가 [!UICONTROL Product Carousel].

<u>예상 결과</u>:

장바구니에 제품을 추가한 후 제품 수량이 두 배가 되지 않아야 합니다. [!UICONTROL Product Grid].

<u>실제 결과</u>:

장바구니에 제품을 추가한 후 제품 수량이 두 배가 됩니다. [!UICONTROL Product Grid].

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오. 

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
