---
title: 'ACSD-48362: 새 주소 대신 기본 배송 주소가 사용됩니다.'
description: ACSD-48362 패치를 적용하여 협상 가능 견적을 사용하여 주문을 할 때 새 주소 대신 기본 배송 주소가 사용되는 Adobe Commerce 문제를 해결합니다.
exl-id: 52f518b6-6f73-42cc-ac1b-c893cd5007fa
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-48362: 새 주소 대신 기본 배송 주소가 사용됩니다

ACSD-48362 패치는 협상 가능 견적을 사용하여 주문을 할 때 새로 추가된 주소 대신 기본 배송 주소가 사용되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치되었습니다. 패치 ID는 ACSD-48362입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

협상 가능 견적을 사용하여 주문을 할 때 새로 추가된 배송 주소 대신 기본 배송 주소가 사용됩니다.

<u>재현 단계</u>:

1. 다음으로 이동하여 B2B 견적 활성화 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. 회사 사용자로 로그인
1. 장바구니에 제품을 추가합니다.
1. 장바구니 페이지로 이동하여 견적을 요청합니다.
1. 고객으로 이동 **[!UICONTROL My Quotes]** 페이지를 만들고 방금 만든 quote 를 선택합니다.
1. 로 이동 **[!UICONTROL Shipping Information]** 고객의 quote 페이지에 있는 섹션입니다.
   * 클릭 **[!UICONTROL Add New Address]**, 양식을 작성하고 주소를 저장합니다( 선택하지 않음). **[!UICONTROL Use as my default billing address]** 또는 **[!UICONTROL Use as my default shipping address]**).
1. 클릭 **[!UICONTROL Send for Review]** 고객의 quote 페이지에 있는
1. Adobe Commerce 관리자로 이동하여 방금 만든 견적을 열고 을 클릭합니다. **[!UICONTROL Send]**.
1. 이제 고객의 견적 페이지로 이동하여 페이지를 새로 고친 다음 을 클릭합니다. **[!UICONTROL Proceed to Checkout]**.
1. 체크아웃 페이지에서 데이터는 새 배송 주소를 선택한 경우에도 기본 배송 주소를 표시합니다.
1. 클릭 **[!UICONTROL Continue]** 주문을 하십시오.

<u>예상 결과</u>:

주문은 체크아웃 페이지에서 기본 배송 주소를 다시 선택하지 않고 새 주소를 사용해야 합니다.

<u>실제 결과</u>:

기본 배송 주소로 주문이 처리됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오. 

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
