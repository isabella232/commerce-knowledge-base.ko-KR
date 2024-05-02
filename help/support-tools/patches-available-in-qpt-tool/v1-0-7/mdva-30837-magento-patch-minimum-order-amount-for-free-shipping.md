---
title: 'MDVA-30837: 무료 배송에 대한 최소 주문 금액'
description: MDVA-30837 패치는 무료 배송 계산에 대한 구성 옵션을 추가하므로 사용자는 소계(또는 총계)를 기준으로 무료 배송을 받기 위한 최소 주문 금액을 구성할 수 있습니다. 이를 통해 세금 및 배송 방법에 대한 로컬 사용자 정의가 가능합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 64716d08-4ce0-40d5-aeb7-242e2aa85bb0
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# MDVA-30837: 무료 배송에 대한 최소 주문 금액

MDVA-30837 패치는 무료 배송 계산에 대한 구성 옵션을 추가하므로 사용자는 소계(또는 총계)를 기준으로 무료 배송을 받기 위한 최소 주문 금액을 구성할 수 있습니다. 이를 통해 세금 및 배송 방법에 대한 로컬 사용자 정의가 가능합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치되었습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* 클라우드 인프라의 Adobe Commerce 2.3.4-p2

**Adobe Commerce 버전과 호환:**

* 클라우드 인프라의 Adobe Commerce 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

패치 MDVA-30837은 구성 설정을 추가하여 **최소 주문 금액** 소계(또는 총계)를 기반으로 무료 배송을 받도록 설정:

* **금액에 세금 포함**: *예/아니요* 사용 가능한 배송 방법 구성에서 확인할 수 있습니다.
   * 날짜 **금액에 세금 포함** 이(가) (으)로 설정됨 *예*&#x200B;최소 주문 금액은 소계 + 세금 - 할인으로 계산됩니다.
   * 날짜 **금액에 세금 포함** 이(가) (으)로 설정됨 *아니요*&#x200B;최소 주문 금액은 소계 - 할인으로 계산됩니다.

<u>재현 단계</u>:

1. 다음으로 이동 **스토어** > 설정 > **구성** > **판매** > **세금** 다음을 설정합니다.

   * 세금 계산 기준 *배송 주소*
   * 국경 간 무역 활성화: *아니요*
   * 카탈로그에 생산 가격 표시: *세금 제외*
   * 배송 가격 표시: *세금 제외*
   * 가격 표시: *세금 제외*
   * 소계 표시: *세금 제외*
   * 배송 금액 표시: *세금 제외*
   * 선물 포장 가격 표시: *세금 제외*
   * 인쇄된 카드 가격 표시: *세금 제외*
   * 주문 합계에 세금 포함: *예*
   * 전체 세금 요약 표시: *예*

1. 다음으로 이동 **판매** > **배송 설정** > **무료 배송** 및 설정 **최소 주문 금액** = *30*.
1. 다음으로 이동 **마케팅** > 프로모션 > **장바구니 가격 규칙** 새 가격 규칙 만들기(자세한 단계는 다음을 참조하십시오.) [장바구니 가격 규칙 만들기](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html) 사용 안내서에서 참조)하십시오.

   * 쿠폰 코드 = *특정 쿠폰*.
   * 조건: 소계가 $25보다 크거나 같음.
   * 조치: 무료 운송 = *품목이 일치하는 배송의 경우*.

1. 가격이 $23.10인 제품을 만듭니다.
1. 기본 세금 규칙에 CA 세금을 추가합니다.
1. 장바구니에 이 제품을 추가합니다.
1. 배송 견적 받기 - 세금 공제 후 총계 = $25.01 및 무료 배송이 적용됩니다.
1. 쿠폰 코드를 적용 - 소계 (세금 제외)가 $23.10이기 때문에 유효하지 않습니다.

<u>예상 결과</u>:

추가 구성 설정(세금 대 금액 포함)이 있습니다. *예*/*아니요* 무료 배송 방법 구성에서:

* 세금에 포함이 로 설정된 경우 *예*&#x200B;최소 주문 금액은 소계 + 세금 - 할인으로 계산됩니다.
* 세금에 포함이 로 설정된 경우 *아니요*&#x200B;최소 주문 금액은 소계 - 할인으로 계산됩니다.

<u>실제 결과</u>:

무료 배송 가격 규칙 조건은 소계만 기준으로 할 수 있는 반면, 무료 배송 방법은 총계만 기준으로 할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
