---
title: 'ACSD-46617: **[!UICONTROL Continue to Checkout]소계가 구성된 최소 주문 수량보다 클 때 ** 버튼이 회색으로 표시됨'
description: ACSD-46617 패치를 적용하여 문제가 발생하는 Adobe Commerce 문제를 **[!UICONTROL Continue to Checkout]**이 구성된 최소 주문 수량보다 큰 경우에도 버튼이 회색으로 표시됩니다.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617: &quot;[!UICONTROL Continue to Checkout]소계가 &quot;보다 큰 경우 &quot; 버튼이 회색으로 표시됨[!UICONTROL Minimum Order Amount]&quot;

이 ACSD-46617 패치는 **[!UICONTROL Continue to Checkout]** 부분합이 구성된 최소 주문 수량보다 큰 경우에도 단추는 회색으로 표시됩니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되었습니다. 패치 ID는 ACSD-46617입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음 **[!UICONTROL Continue to Checkout]** 부분합이 구성된 최소 주문 수량보다 큰 경우에도 단추는 회색으로 표시됩니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자로 이동 > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** 다음을 설정합니다.
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. 만들기 [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. 가격이 $25인 제품을 만듭니다.
1. 제품을 장바구니에 추가합니다.
1. 장바구니로 이동하여 $5를 선택합니다. **[!UICONTROL Flat Rate shipping]** 메서드 및 쿠폰 코드를 적용합니다.
1. 체크아웃으로 이동하여 배송을 완료한 다음 **[!UICONTROL Paytment]** 섹션.
1. 장바구니로 돌아갑니다.

<u>예상 결과</u>:

총 합계 $2.4가 소요량인 $2보다 많아 최소 주문량과 관련된 오류는 없다.

<u>실제 결과</u>:

* 총액 2.4달러가 최소 주문금액 2달러보다 큰 경우에도 최소 주문금액과 관련된 오류가 있다.
* 다음 **[!UICONTROL Continue to Checkout]** 단추가 회색으로 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
