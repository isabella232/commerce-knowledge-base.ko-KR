---
title: 'MDVA-30972: 주문 상태가 REST API를 통해 잘못된 선적을 만들었습니다.'
description: MDVA-30972 패치는 REST API를 통해 배송을 생성하는 동안 주문 상태가 잘못 변경되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다.
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972: REST API를 통해 생성된 주문 상태 잘못된 배송

MDVA-30972 패치는 REST API를 통해 배송을 생성하는 동안 주문 상태가 잘못 변경되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* 클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0에서 2.4.2로

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음을 포함한 주문에 대해 REST API를 통해 책임자로부터 부분 선적이 생성되는 경우 *사기 혐의* 주문 상태, 주문 상태가 다음으로 변경됨 *처리 중*. 다음 위치에 있어야 합니다. *사기 혐의*.

<u>전제 조건</u>:

* PayPal EC 또는 다른 온라인 결제 방법을 설정합니다.
* REST API에 대한 통합이 설정되었습니다.

<u>재현 단계</u>:

1. 두 개 이상의 항목으로 주문을 만듭니다.
1. 에 로그인 **관리자** > **판매** > **주문 수**. 방금 생성한 주문을 엽니다.
1. 주문 세부 사항 페이지에서 아래로 스크롤하여 **주문 합계**. 을(를) 클릭합니다 **상태** 드롭다운 및 선택 *사기 혐의*. 그런 다음 **의견 제출** 단추를 클릭합니다.
1. 주문에 이 기능이 있는지 확인합니다. *사기 혐의* 지금 상태.
1. REST API를 사용하여 주문에서 한 품목에 대한 납품을 생성합니다.

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. Admin에서 주문을 다시 열고 상태를 확인합니다.

<u>예상 결과</u>:

* 주문 상태 = *사기 혐의*.
* 동일한 선적이 책임자로부터 생성된 경우 주문 상태가 변경되지 않습니다.

<u>실제 결과</u>:

주문 상태 = *처리 중*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
