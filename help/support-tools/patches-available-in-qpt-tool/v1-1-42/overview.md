---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: 이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.1.42.
feature: Tools and External Services
role: Admin, Developer
exl-id: 49f7ebd6-7a5f-49da-8fac-c3c2b73b52c1
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool] (QPT) v1.1.42

이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.1.42.

QPT v1.1.42에는 다음 패치가 포함됩니다.

1. **ACSD-53658**: 다음의 문제를 해결합니다. *[!UICONTROL Recently Viewed]* 스토어 보기에서 제품 데이터가 제대로 업데이트되지 않습니다.
1. **ACSD-54626**: 새 구매 발주 규칙을 만들 수 없는 문제가 해결되었습니다(`createPurchaseOrderApprovalRule`) `NUMBER_OF_SKUS` GraphQL을 통한 속성
1. **ACSD-53845**: 다음과 같은 경우 MySQL 연결 시간 초과 문제를 해결합니다. `consumer max_messages` = 0.
1. **ACSD-54890**: 다음의 문제를 해결합니다. `aggregate_sales_report_bestsellers_data` 다음 원인으로 인해 MySQL 오류가 발생합니다. `/tmp` 디스크 공간이 부족합니다.
1. **ACSD-55112**: 이(가) 발생하는 문제를 수정합니다. *[!UICONTROL Submit review]* 없이 단추를 여러 번 클릭할 수 있습니다. [!DNL Google reCAPTCHA v3] 유효성 검사.
1. **ACSD-54264**: 오류 메시지가 표시되는 문제를 수정합니다 *요청한 속성을 업데이트할 수 없습니다. 행 ID: store_id* 고객이 다른 스토어 뷰에서 협상 가능한 견적을 사용하여 체크아웃하려고 할 때 표시됩니다.
1. **ACSD-54418**: 고정 할인 금액이 동적으로 가격이 책정된 번들의 각 하위 제품에 잘못 적용되는 문제를 수정합니다.
1. **ACSD-55238**: 빈 제품 메타 설명을 저장할 때 발생하는 문제를 해결합니다.
1. **ACSD-54966**: 이전 주문이 실패한 경우 고객당 사용이 제한된 쿠폰 코드를 다시 사용할 수 없는 문제를 수정합니다.
1. **ACSD-54060**: 다른 범위에 할당된 다른 제품의 하위 항목인 경우 제한된 관리자가 제품을 저장할 수 없는 문제를 수정합니다.
1. **ACSD-48910**: 주문이 청구되고 배송된 후 0이 아닌 수량이 있더라도 여러 출처에 할당된 번들 제품의 재고가 부족한 문제를 수정합니다.
1. **ACSD-55381**: 쿼리할 때 내부 서버 오류 수정 `configurable_product_option_uid` 및 `configurable_product_option_value_uid` B2B의 필드 *[!UICONTROL Requisition list]* GraphQL을 통해
1. **ACSD-55628**: 회사 등록 양식에 파일을 업로드하고 상점의 고객 속성에 대한 파일을 바꾸는 문제가 수정되었습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
