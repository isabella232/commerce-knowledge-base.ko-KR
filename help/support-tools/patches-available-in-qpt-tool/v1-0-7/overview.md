---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.0.7'
description: 이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.0.7.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.7 개요

이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.0.7.

QPT v1.0.7에는 다음 패치가 포함됩니다.

1. **MDVA-29148**: API 호출을 통해 제품을 만들 때 의 제품 사용자 지정 속성인 문제를 수정합니다. `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (Multiselect와 유사) 유형은 페이로드에 값이 제공되지 않으면 기본값을 사용하지 않습니다.
1. **MDVA-29389**: 고급 보고에서 다음과 같은 문제를 수정합니다. `analytics_collect_data` cronjob은 이렇게 말합니다: *포트는 호스트 매개 변수 내에 구성해야 합니다(예: localhost:3306).*.
1. **MDVA-30594**: FPT가 구성된 경우 체크아웃 중에 여러 주소가 있는 주문을 저장할 수 없는 문제를 수정합니다.
1. **MDVA-30782**: 장바구니 규칙에 관계없이 동적 블록이 표시되는 문제를 수정합니다.
1. **MDVA-30815**: 검색 결과 페이지에 표시할 검색 결과의 수를 변경할 때 발생하는 문제를 수정합니다.
1. **MDVA-30837**: 사용자가 소계(또는 총계)를 기반으로 무료 배송을 받기 위한 최소 주문 금액을 구성할 수 있도록 무료 배송 계산에 대한 구성 옵션을 추가합니다.
1. **MDVA-30945**: 카트를 업데이트할 때 치명적인 오류 메시지가 표시되는 문제를 수정합니다 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **MDVA-30972**: 사용자 지정 순서 상태가 (으)로 변경된 문제가 해결되었습니다. *처리 중* WebApi를 사용하여 부분 선적을 만든 후.
1. **MDVA-31007**: 사용자 지정 주소 속성이 내 계정 영역 및 백엔드의 주문 세부 사항 페이지에 올바르게 표시되지 않는 문제를 수정합니다.
1. **MDVA-31021**:에서 성능 문제가 발생하는 문제를 수정합니다 `module-catalog-import-export/Model/Import/Product/Option.php`. 에 ~100만 개 이상의 레코드가 있는 경우 `catalog_product_option` 표: 단일 제품이 포함된 새 CSV의 유효성을 검사하는 데 10초 미만이 소요됩니다.
1. **MDVA-31224**: 의 성능을 개선합니다. `catalog_product_price` 번들 제품에 대한 작업을 다시 색인화합니다.
1. **MDVA-31282**:에서 두 번 권한 부여가 발생하는 문제를 수정합니다 [!DNL Paypal PayFlow Pro] Adobe Commerce. 이중 허가는 우회를 하는 효과도 있다 [!DNL PayFlow Pro's] 사기 필터 및 두 배의 거래 수수료.
1. **MDVA-31343**: 제거된 본문 클래스의 문제를 수정합니다 `page-layout-category-full-width` 범주가 예약되는 경우.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
