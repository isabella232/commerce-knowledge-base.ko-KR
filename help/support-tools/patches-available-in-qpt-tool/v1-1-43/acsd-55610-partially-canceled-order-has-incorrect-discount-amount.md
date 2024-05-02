---
title: 'ACSD-55610: 부분적으로 취소된 주문의 할인 금액이 잘못됨'
description: ACSD-55610 패치를 적용하여 부분적으로 취소된 주문에 잘못된 할인 금액이 있는 Adobe Commerce 문제를 해결합니다.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: f4cca4fa-dc04-4c86-9176-c648b1d0e732
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-55610: 부분적으로 취소된 주문의 할인 금액이 잘못됨

ACSD-55610 패치는 부분적으로 취소된 주문에 잘못된 할인 금액이 있는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.43이 설치되었습니다. 패치 ID는 ACSD-55610입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

일부 취소된 주문의 할인 금액이 잘못되었습니다.

<u>재현 단계</u>:

1. 장바구니 가격 규칙을 만듭니다.

   * *[!UICONTROL Rule Name]*: *겨울 판매*
   * *[!UICONTROL Active]* = *예*
   * *[!UICONTROL Websites]* = *기본 웹 사이트*
   * 모든 고객 그룹을 선택합니다.
   * 특정 쿠폰을 선택합니다.
   * *[!UICONTROL Coupon Code]*: *WINTER10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *소계(제외) 세금)이 75보다 크거나 같음*
   * 적용 *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *예*

1. 가격이 100으로 설정된 제품 3개를 만듭니다.
1. 세 제품을 장바구니에 추가합니다.
1. 쿠폰을 적용하세요.
1. 주문하십시오.
1. 주문의 한 품목에 대한 송장을 발행하여 발송합니다.
1. 나머지 두 항목은 취소해 주십시오.
1. 다음 확인: `base_discount_canceled` 열.

<u>예상 결과</u>:

할인 금액 `base_discount_cancelled` 을 올바르게 반영합니다.

<u>실제 결과</u>:

다음 `base_discount_cancelled` 은(는) 올바르지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
