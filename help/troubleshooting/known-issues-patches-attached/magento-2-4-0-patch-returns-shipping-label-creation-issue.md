---
title: 'Adobe Commerce 2.4.0 패치: 배송 레이블 생성 문제를 반환합니다.'
description: 이 문서에서는 고객 반품에 대한 배송 레이블을 인쇄하는 데 문제가 있는 경우 알려진 Adobe Commerce 2.4.0 문제에 대한 패치를 제공합니다.
exl-id: f78f8d7e-29e9-4d6c-83f6-cd5afa1d7d9c
feature: B2B, Orders, Returns, Communications, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 패치: 배송 레이블 생성 문제를 반환합니다.

이 문서에서는 고객 반품에 대한 배송 레이블을 인쇄하는 데 문제가 있는 경우 알려진 Adobe Commerce 2.4.0 문제에 대한 패치를 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.0
* Adobe Commerce 온-프레미스 2.4.0

## 문제

<u>재현 단계:</u>

1. FedEx, DHL, UPS, USPS의 핵심 배송 방법 중 하나로 주문을 완료하십시오.
1. 이 주문에 대한 반품을 만들고 승인합니다.
1. 권한이 있는 을(를) 엽니다 **반환 정보** 페이지를 클릭하고 **배송 레이블 만들기** 단추를 클릭합니다.
1. 배송 방법을 선택하고 패키지에 제품을 추가한 다음 [저장]을 클릭합니다.

<u>예상 결과:</u>

배송 레이블이 정상적으로 생성되었으며 다음과 같은 메시지가 표시됩니다. *배송 레이블을 만들었습니다.*

<u>실제 결과:</u>

다음 **반환 정보** 페이지가 손상되어 반환 정보 페이지에 다음과 같은 오류 메시지가 표시됩니다. *이 섹션에 저장되지 않은 일반 정보가 변경되었습니다. 이 탭에 잘못된 데이터가 포함되어 있습니다.*.

## 솔루션

적용 [patch](assets/MC-35984-2.4.0-CE-composer.patch.zip) 이 문서에서 제공됩니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MC-35984-2.4.0-CE-composer.patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)

이 패치는 다음 두 위치에서 모두 다운로드할 수 있습니다. `.git` 및 `.composer`, 포맷 [Adobe Commerce 다운로드](https://magento.com/tech-resources/download) 페이지, 아래 **패치** 왼쪽 열 탐색에서. MC-35984 패치를 검색합니다.

## 패치 적용 방법

자세한 내용은 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 지원 지식 페이지.

## 지원 기술 자료의 관련 자료:

* [Adobe Commerce 2.4.0 알려진 문제: storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 알려진 문제: 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: &quot;내 장바구니에 선택 항목 추가&quot; 버튼이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: Braintree 결제 방법이 여러 주소 체크아웃에 표시되지 않음](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 알려진 문제: 주문 표시 오류](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0의 배송 라벨 작성 알려진 문제](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
