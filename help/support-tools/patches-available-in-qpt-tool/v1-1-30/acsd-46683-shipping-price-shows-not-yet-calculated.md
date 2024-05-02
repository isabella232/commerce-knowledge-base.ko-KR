---
title: 'ACSD-46683: 배송 가격 표시 *아직 계산되지 않음*'
description: ACSD-46683 패치를 적용하여 배송비가 *아직 계산되지 않음*으로 표시되는 Adobe Commerce 문제를 해결합니다.
exl-id: 77986612-87b7-4f50-afaf-1cfe9a4feb6f
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683: 배송 가격 표시 *아직 계산되지 않음*

ACSD-46683 패치는 배송 가격이 표시되는 문제를 해결합니다 *아직 계산되지 않음*. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되었습니다. 패치 ID는 ACSD-46683입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

배송 가격은 다음과 같습니다. *아직 계산되지 않음*.

<u>전제 조건</u>:

Adobe Commerce Inventory management(MSI) 모듈이 설치되었습니다.

<u>재현 단계</u>:

1. 간단한 제품을 만들고 가격을 다음으로 설정 *US$34*.
1. 무료 배송 배송 방법을 구성합니다.
1. 하나 이상의 게재 방법을 구성합니다.
1. 다음으로 이동 **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** 새 규칙을 만듭니다.
   * 이름 = *75개 더*
   * 쿠폰 = 없음
   * 우선 순위 = 1
   * 조건: 소계가 보다 크거나 같음 *75달러*
   * 작업:
      * 운송 금액에 적용 = 예
      * 후속 규칙 버리기 = 아니요
      * 무료 출하 = 품목이 일치하는 출하의 경우
1. 다른 장바구니 가격 규칙을 만듭니다.
   * 이름 = *35off*
   * 우선 순위 = 0
   * 쿠폰 = 특정 쿠폰
   * 쿠폰 코드 = 35off
   * 작업:
      * 적용 = 제품 가격 할인의 퍼센트
      * 할인 금액 = 35
      * 운송 금액에 적용 = 아니오
      * 후속 규칙 무시 = 예
      * 무료 배송 = 아니오
1. 가게 앞을 열고 소계가 75달러를 초과하도록 장바구니에 세 가지 제품을 추가합니다.
1. 게스트로 체크아웃을 진행합니다.
1. 배송 단계에서 다음을 선택합니다 **$0 - 무료 배송** 결제 단계로 진행합니다.
1. 다음 확인: [!UICONTROL Order Summary] 결제 단계에서 사용할 수 있습니다. 다음을 표시합니다. *[!UICONTROL $0 - Free Shipping - Free]*.
1. 쿠폰 코드 적용 *35off*, 소계를 업데이트하여 75 달러 미만으로 만듭니다.
1. 확인 [!UICONTROL Order Summary] 결제 단계에서 사용할 수 있습니다.

<u>예상 결과</u>:

다음 메시지가 표시됩니다. *선택한 배송 방법을 사용할 수 없습니다. 이 주문에 대한 다른 배송 방법을 선택하십시오.*

<u>실제 결과</u>:

배송 가격이 표시됩니다. *아직 계산되지 않음*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
