---
title: 'ACSD-55352: 보상 포인트가 있는 대변 메모 생성'
description: ACSD-55352 패치를 적용하여 고객 보상 포인트가 포함된 부분 대변 메모를 만든 후 주문 상태가 *마감됨*으로 변경되고 관리자 주문 페이지에서 대변 메모 옵션이 사라지는 Adobe Commerce 문제를 해결합니다.
feature: Checkout, Orders
role: Admin, Developer
exl-id: 33ceb2e9-3cd5-4472-941a-e06c5c534f4a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-55352: 보상 포인트를 사용하여 대변 메모 생성

ACSD-55352 패치는 고객 보상 포인트가 있는 부분 대변 메모를 작성한 후 주문 상태가 로 변경되는 문제를 해결합니다. *종료됨* 및 대변 메모 옵션은 관리자 주문 페이지에서 사라집니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44가 설치되어 있습니다. 패치 ID는 ACSD-55352입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객 보상 포인트가 있는 부분 대변 메모를 생성하면 주문 상태가 다음으로 변경됩니다. *종료됨* 및 대변 메모 옵션은 관리자 주문 페이지에서 사라집니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자에 로그인합니다.
2. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. 두 개의 요금을 추가합니다.
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *통화 포인트*
      * *[!UICONTROL Rate]* = *10*
      * *[!UICONTROL Upper Boundary]* = *10*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *통화-포인트*
      * *[!UICONTROL Rate]* = *10*
      * *[!UICONTROL Upper Boundary]* = *10*
4. 다음과 같은 가격으로 간단한 제품 만들기 *100달러* 및 포함 *수량* : *10*.
5. 상점에서 고객을 만듭니다.
6. 백엔드로 다시 이동 : **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > 추가 *10* 고객을 구하십시오.
7. 상점으로 이동한 다음 고객이 이전에 만든 것으로 로그인합니다.
8. 제품을 장바구니에 추가 *수량* : *10*.
9. 다음으로 이동 **[!UICONTROL Checkout]** 및 사용 가능한 *10* 메시지가 표시되면 포인트를 보상하고 주문을 배치합니다.
10. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** 그리고 그 주문을 배송해주세요
11. 다음으로 이동 [!UICONTROL Credit Memo] 및 업데이트 *환불할 수량* 끝 *8*.
12. 확인 **[!UICONTROL Refund Reward Points]** 확인란 및 클릭 **[!UICONTROL Refund offline]**.
13. 주문에서 나머지 2개의 제품은 다음을 사용하여 환불해 보십시오. [!UICONTROL Credit Memo].

<u>예상 결과</u>:

* 관리자가 만드는 항목 [!UICONTROL Credit Memo] 나머지 두 제품을 반품합니다.
* 주문 상태는 입니다. *완료됨*.

<u>실제 결과</u>:

* 더 이상 만들 수 없음 [!UICONTROL Credit Memo].
* 주문 상태는 입니다. *종료됨*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
