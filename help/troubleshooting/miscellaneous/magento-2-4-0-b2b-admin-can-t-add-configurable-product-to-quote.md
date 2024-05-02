---
title: Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음
description: 이 문서에서는 B2B Quote 를 관리할 때 Commerce 관리자의 알려진 문제에 대해 설명합니다. **SKU**별로 구성 가능한 제품을 Quote에 추가할 수 없습니다. **Quote에 추가** 버튼을 클릭하면 **Quote** 편집 페이지가 로드되지 않고 제품을 구성하고 변경 사항을 저장할 수 없습니다. 이 문제는 관리자가 **SKU**별 제품을 주문에 추가하거나 **Advanced Checkout** (**Admin** &gt; **Customers** &gt; **All Customers** &gt; **Manage Shopping Cart** ** **)에서 **SKU**별 제품을 추가할 때도 발생합니다. 이 문제는 Adobe Commerce 2.4.1용 패치에서 해결됩니다.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음

이 문서에서는 B2B Quote 를 관리할 때 Commerce 관리자의 알려진 문제에 대해 설명하지만 다음 방법으로 구성 가능한 제품을 추가할 수 없습니다. **SKU** 을 참조하십시오. 클릭 시 **견적에 추가** 단추, **견적** 편집 페이지 로드가 중단되어 제품을 구성하고 변경 사항을 저장할 수 없습니다. 이 문제는 관리자 가 다음 방법으로 제품을 추가할 때도 발생합니다. **SKU** 주문 또는 다음 방법으로 제품 추가 **SKU** 위치: **고급 체크아웃** (**관리자** > **고객** > **모든 고객** > **고객 편집** > **장바구니 관리**). 이 문제는 Adobe Commerce 2.4.1용 패치에서 해결됩니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0
* 클라우드 인프라의 Adobe Commerce 2.4.0

## 문제

<u>전제 조건</u>

* Adobe Commerce 2.4.0이 설치되어 있습니다.
* B2B가 설치되었습니다.
* B2B 기능을 다음으로 설정 **회사 활성화 =**  *예* , **공유 카탈로그 활성화 =**  *아니요* , 및 **B2B 견적 활성화 =**  *예*.
* 고객 계정을 만듭니다.
* 이전에 만든 고객을 회사 관리자로 사용하여 회사 계정을 만듭니다.
* 간단한 제품 만들기(예: name &amp; **SKU** = TEST SIMPLE 1) 이 할당되지 않은 경우 **기본값(일반)**.
* 회사 관리자가 위에서 만든 간단한 제품을 사용하여 견적을 요청하도록 합니다(예: TEST SIMPLE 1).

<u>재현 단계</u>

1. Commerce 관리 패널로 이동합니다.
1. 다음으로 이동 **영업 > 견적**.
1. 를 엽니다. **견적**.
1. 다음을 클릭합니다. **SKU별 제품 추가** 단추를 클릭합니다.
1. 다음을 입력합니다. **SKU** 다음 위치에 있는 다른(예: TEST SIMPLE 2) 제품 **SKU 입력** 입력 필드.
1. 유효한 수량을 입력하십시오. **수량** 입력 필드.
1. 다음을 클릭합니다. **견적에 추가** 단추를 클릭합니다.

<u>예상 결과</u>

* 다음 **견적에 추가되지 않은 제품** 그리드, 이름 및 **SKU** 을(를) 만든 제품의 예상대로 표시합니다.
* 제품이 구성되면 관리자는 제품에 추가할 수 있습니다. **견적** 을(를) 클릭하여 **견적에 제품 추가** 단추입니다.

<u>실제 결과</u>

* 다음 **견적에 추가되지 않은 제품** 그리드, 이름 및 **SKU** 을(를) 만든 제품의 경우 이 표시되지 않습니다.
* 다음 **견적** 페이지 로드가 중단되었습니다.

## 추천

현재 B2B 견적 편집에서는 이 문제에 대한 해결 방법이 없지만 주문 및 장바구니 관리의 경우 **제품 목록** 을 통해 추가하는 대신 **SKU**. 이 문제를 해결하기 위한 패치는 2020년 4분기 릴리스될 예정인 Adobe Commerce 2.4.1에서 사용할 수 있습니다.

## 관련 읽기

* [Adobe Commerce 2.4.0 알려진 문제: 고객의 활동에 대한 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: Storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 알려진 문제: 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: 주문 표시 오류](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
