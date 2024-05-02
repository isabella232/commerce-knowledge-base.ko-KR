---
title: 'Adobe Commerce 2.4.1 알려진 문제: PayPal Braintree으로 체크아웃할 때 오류 발생'
description: 이 문서에서는 PayPal Braintree 결제를 사용하고 여러 주소 선적을 선택한 경우 체크아웃의 청구 단계에서 오류 메시지가 표시되며 사라지는 알려진 Adobe Commerce 2.4.1 문제에 대해 설명합니다.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 알려진 문제: PayPal Braintree을 사용하여 체크아웃할 때 오류 발생

이 문서에서는 PayPal Braintree 결제를 사용하고 여러 주소 선적을 선택한 경우 체크아웃의 청구 단계에서 오류 메시지가 표시되며 사라지는 알려진 Adobe Commerce 2.4.1 문제에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.1
* Adobe Commerce 온-프레미스 2.4.1

## 문제

PayPal Braintree 결제를 사용하고 여러 주소 선적을 선택한 경우 체크아웃 청구 단계에서 오류 메시지가 팝업되고 사라집니다.

<u>재현 단계:</u>

1. 상점 첫 화면에서 고객으로 로그인합니다 (관리자 권한으로 활성화된 경우 선택적으로 게스트 체크아웃이 될 수 있음).
1. 장바구니에 제품을 추가합니다.
1. 를 클릭하여 장바구니 미리 보기를 엽니다.
1. 클릭 **장바구니 보기 및 편집**.
1. 장바구니 페이지에서 **여러 주소로 체크아웃**.
1. 클릭 **배송 정보로 이동** 주소를 지정합니다.
1. 클릭 **청구 정보로 계속**.
1. 선택 **PayPal Braintree** 을(를) 클릭하고 **PayPal** 단추를 클릭합니다.
1. 팝업 창에서 다음을 클릭합니다. **동의 및 지불**.

<u>예상 결과:</u>

아무런 오류 없이 주문이 완료되었습니다.

<u>실제 결과:</u>

주문이 들어갔지만 오류가 발생했습니다. 다음 *PayPal 체크아웃을 초기화할 수 없습니다. 스토어 소유자에게 문의하십시오.*.  오류가 잠시 표시되었다가 사라집니다.

## 수정

주문발주가 차단되지 않으므로, 해결 단계를 수행할 필요가 없습니다.
