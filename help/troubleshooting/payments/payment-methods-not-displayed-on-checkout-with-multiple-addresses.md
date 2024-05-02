---
title: 여러 주소가 있는 체크아웃 시 결제 방법이 표시되지 않음
description: 이 문서에서는 여러 배송 주소를 지정할 때 결제 방법의 대부분이 체크아웃 시 표시되지 않는데, 그 이유는 이 기능이 Cybersource에 대해서만 구현되기 때문입니다.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# 여러 주소가 있는 체크아웃 시 결제 방법이 표시되지 않음

이 문서에서는 여러 배송 주소를 지정할 때 결제 방법의 대부분이 체크아웃 시 표시되지 않는데, 그 이유는 이 기능이 Cybersource에 대해서만 구현되기 때문입니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.x.x
* 클라우드 인프라의 Adobe Commerce 2.x.x

>[!NOTE]
>
>핵심 Adobe Commerce Cybersource 결제 통합은 2.3.3부터 더 이상 사용되지 않으며 2.4.0에서 완전히 제거됩니다. 사용 [공식 연장](https://marketplace.magento.com/cybersource-global-payment-management.html) marketplace에서 가져옵니다.

## 문제

<u>전제 조건</u>: Commerce 관리에서 PayPal 및 Cybersource 결제 방법을 활성화하고 구성하고 스토어에 대해 다중 배송을 활성화합니다.

<u>재현 단계</u>:

1. 상점 첫 화면에서 장바구니에 여러 제품을 추가합니다.
1. 장바구니 페이지로 이동합니다.
1. 클릭 **여러 주소로 체크아웃**.
1. 로그인하거나 계정을 만듭니다.
1. 복수 주소로 출하 페이지의 주소 간에 제품을 분할합니다.
1. 클릭 **배송 정보로 이동**.
1. 각 선적에 대해 운송 방법을 선택합니다.
1. 클릭 **청구 정보로 계속**.

<u>예상 결과</u>: PayPal 및 Cybersource를 결제 옵션으로 사용할 수 있습니다.

<u>실제 결과</u>: Cybersource만 사용 가능한 결제 옵션으로 나타납니다.

## 원인

현재 Cybersource는 버전 2.2.4부터 시작되는 다중 배송 체크아웃을 위한 유일한 지원 라이브 결제 방법입니다. 다중 배송에 대한 지원은 각 결제 수단별로 하나씩 구축될 가능성이 높다. 현재로서는 정확한 일자 또는 릴리스 번호를 제공할 수 없습니다.
