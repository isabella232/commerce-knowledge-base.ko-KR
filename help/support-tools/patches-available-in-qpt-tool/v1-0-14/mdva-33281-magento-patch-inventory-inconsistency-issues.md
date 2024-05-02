---
title: 'MDVA-33281 패치: 인벤토리 불일치 문제'
description: MDVA-33281 패치는 세 가지 인벤토리 불일치 문제를 해결합니다. 문제 섹션 아래에서 연결된 문제를 클릭하여 이러한 오류를 재현하는 단계를 확인합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14가 설치된 경우 사용할 수 있습니다.
exl-id: adba9728-6e42-467e-943d-cf8af0bec353
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-33281 패치: 인벤토리 불일치 문제

MDVA-33281 패치는 세 가지 인벤토리 불일치 문제를 해결합니다. 문제 섹션 아래에서 연결된 문제를 클릭하여 이러한 오류를 재현하는 단계를 확인합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14가 설치되어 있습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.3.5-p1

**Adobe Commerce 버전과 호환:**

클라우드 인프라의 Adobe Commerce 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이 패치는 다음과 같은 인벤토리 불일치 문제를 수정합니다.

* **PHP 치명적인 오류** 실행 시 `bin/magento inventory:reservation:list-inconsistencies` 잘못된 SKU 매개 변수 유형으로 인해 CLI에서 오류가 발생했습니다.
* **중복 데이터** 불일치 목록에 있습니다.
* **새 예약** 은 주문 전에 생성됩니다(주문 후 예약에 따른 이전 실현). 주문 배치에서 오류가 발생한 경우 보상을 위해 추가 예약이 추가됩니다.

>[!NOTE]
>
>예기치 않게 많은 수의 30112이 있는 문제를 해결하는 패치 MDVA-CFP도 있습니다. [예약 불일치](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) 개발자 설명서에서 `inventory_reservation` 테이블. 해결 방법은 을 참조하십시오. [MDVA-30112 Magento 패치: 대량 예약 불일치](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md) 을 참조하십시오.

## PHP 치명적인 오류

<u>재현 단계</u>:

실행할 때 PHP 치명적인 오류 `bin/magento inventory:reservation:list-inconsistencies`.

예약 불일치 목록을 보려면 운영 서버에 로그인하고 CLI에서 다음 명령을 실행합니다(-r switch - raw output).

<pre>bin/magento 인벤토리:reservation:목록 불일치 -r</pre>

<u>예상 결과</u>:

예약 불일치 목록이 만들어집니다. 이는 다음 형식으로 반환됩니다

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>실제 결과</u>:

PHP 치명적인 오류가 출력됩니다.

## 중복 데이터

중복 데이터는 `inventory_reservation table`.

<u>재현 단계</u>:

예약 불일치 문제를 해결하려면 다음 명령을 실행합니다.

<pre>INVENTORY_RESERVATION GROUP BY METADATA, sku, quantity HAVING COUNT(*) &gt; 1에서 *, COUNT(*) 선택</pre>

<u>예상 결과</u>:

중복 항목 없음.

<u>실제 결과</u>:

중복 항목이 있습니다.

## 새 예약

<u>재현 단계</u>:

주문 전에 생성된 새 예약:

1. 데이터베이스를 가져옵니다.
1. 실행 `bin/magento setup:upgrade` 터미널에 있습니다.
1. 실행을 통한 불일치 나열 `bin/magento inventory:reservation:list-inconsistencies        -i -r` 터미널에 있습니다.

<u>예상 결과</u>:

루프가 없고 훨씬 더 빠른 결과가 나옵니다.

<u>실제 결과</u>:

동일한 결과가 무한 루프에 표시되거나 명령이 `memory_limit`, 시스템 설정에 따라 다릅니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
