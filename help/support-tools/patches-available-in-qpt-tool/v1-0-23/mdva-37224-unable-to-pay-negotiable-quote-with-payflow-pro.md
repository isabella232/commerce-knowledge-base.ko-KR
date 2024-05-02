---
title: 'MDVA-37224: PayFlow Pro로 "협상가능 견적"을 지급할 수 없음'
description: MDVA-37224 패치는 고객이 Paypal PayFlow Pro로 **협상 가능한 견적**을 결제할 수 없는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37224입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.
exl-id: df75b38d-64c8-46b5-85ff-7606ce1dfd34
feature: B2B, Orders, Payments, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-37224: PayFlow Pro로 &quot;협상가능 견적&quot;을 지급할 수 없음

MDVA-37224 패치는 고객이 비용을 지불할 수 없을 때 발생하는 문제를 해결합니다 **협상 가능 견적** Paypal PayFlow Pro와 함께. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23이 설치되었습니다. 패치 ID는 MDVA-37224입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

* 이 패치는 클라우드 인프라 2.3.6-p1의 Adobe Commerce용으로 설계되었습니다
* 이 패치는 Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.3-2.4.2-p1과도 호환됩니다

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>전제 조건</u>:

* B2B 모듈이 설치된 Adobe Commerce
* 회사 기능 활성화됨
* **협상 가능 견적** 활성화된 기능
* 회사 사용자가 있습니다.
* PayPal PayFlow Pro 결제 방법을 활성화하고 구성합니다.
* PayPal PayFlow Pro 결제 방법은 B2B에 허용됩니다.
* 가격이 다른 2개 제품이 만들어졌습니다

<u>재현 단계</u>:

1. 가게 문 열어
1. 추가 **제품 1** 장바구니로.
1. 만들기 **협상 가능 견적** 대상 **제품 1**.
1. 추가 **제품 2** 장바구니로.
1. 책임자로부터 다음 내용에 동의하십시오. **협상 가능 견적** 3단계에서 만들어집니다.
1. 상점 앞에서 열어 **협상 가능 견적** 체크아웃을 진행하십시오.
1. 다음 항목 선택 **결제 방법** = *PayPal PayFlow 프로* 위치: **검토 및 지급** 단계.
1. 주문하십시오.

<u>예상 결과</u>:

* 예상대로 주문이 성공적으로 완료되었습니다.
* PayPal은 예상대로 고객에게 올바른 정보가 포함된 이메일을 보냅니다.

<u>실제 결과</u>:

* 웹 페이지가 중단되고 주문이 완료되지 않습니다.
* PayPal은 이 예제와 유사하게 값이 0인 고객에게 확인을 보냅니다.

```php
Order ID: A1xxxxxxxxx
Order Placed: Monday, April 21, 2021 01:12:12 PM PDT

Shipping Amount: $0.00
Tax Amount: $0.00
Amount of Transaction: $0.00
Payment Type: Visa

BILL TO
--------
US
```


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* 
   * [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션.
