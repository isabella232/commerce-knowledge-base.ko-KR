---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.34'
description: 이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.1.34.
feature: Tools and External Services
role: Admin
exl-id: 79998832-26cb-4c11-a505-08c3382f86d4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool] (QPT) v1.1.34

이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.1.34.

QPT v1.1.34에는 다음 패치가 포함됩니다.

1. **ACSD-52277**: 관리자에서 새 주문을 만들 때 저장소 보기를 선택한 후 관리자 사용자가 제대로 리디렉션되지 않는 문제를 해결합니다.
1. **ACSD-50813**: 관리자가 SKU에서 를 사용하여 슬래시가 포함된 번들 제품을 추가할 수 없는 문제를 해결했습니다. [!UICONTROL Add Products by SKU] 관리 순서에 대한 기능입니다.
1. **ACSD-51630**: 대량의 시스템 메시지가 관리 페이지 다운로드를 지연시키는 문제를 해결합니다.
1. **ACSD-51853**: 를 사용할 때 복사된 텍스트 스타일이 적용되지 않는 문제를 해결합니다 [!DNL Page Builder].
1. **ACSD-52160**: 장바구니 가격 규칙에 대한 제품 유효성 검사 결과가 규칙 조건에 따라 올바르게 평가되지 않는 문제를 수정합니다 *항목이 이러한 모든/임의 조건이 true인 장바구니에서 발견됨/발견되지 않음*.
1. **ACSD-51636**: 필요한 모든 역할 및 권한이 있음에도 불구하고 관리자가 고객 계정 섹션에서 새 사용자를 추가할 수 없는 문제를 해결했습니다.
1. **ACSD-51739**: 다음과 같은 경우에 오류가 반환되는 문제를 수정합니다. `structure_id` 다음 위치에 요청됨: `CompanyTeam` GraphQL 요청.
1. **ACSD-51857**: 의 성능이 저하되는 문제가 해결되었습니다. `aggregate_sales_report_bestsellers_data` 크론 보고서가 크기에 영향을 줌 `sales_order` 및 `sales_order_item` 데이터베이스 테이블.
1. **ACSD-48448**: 주문 취소 중에 발생하는 경쟁 조건 문제로 인해 의 항목이 중복되는 문제를 해결합니다. *inventory_reservation* 테이블.
1. **ACSD-52689**: 이미지를 업로드할 수 없는 문제를 해결했습니다. [!DNL Amazon S3] rest API를 사용하는 저장소입니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
