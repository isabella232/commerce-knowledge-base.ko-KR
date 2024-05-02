---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: 이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.1.31.
exl-id: 0d93619e-0ae6-4dba-9b76-8aeb026c456d
feature: Tools and External Services
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool] (QPT) v1.1.31

이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.1.31.

QPT v1.1.31에는 다음 패치가 포함됩니다.

1. **ACSD-50817**: cron 작업 최적화 `sales_clean_quotes` 에 복합 인덱스를 추가하여 더 빠르게 실행 `store_id` 및 `updated_at` quote 테이블에 있는 열
1. **ACSD-50345**: 다음과 같은 문제가 해결되었습니다. [!DNL Google reCAPTCHA v2] 실패한 결제를 제출한 후 다시 로드되지 않음, [!DNL Google reCAPTCHA v3 Invisible] 은(는) 체크아웃 상태에서 작동하지 않으며 주문을 할 수 없습니다. [!UICONTROL PlaceOrder] 이벤트가 트리거되지 않았습니다.
1. **ACSD-49392**: 번들 제품에 대한 부분 환불 후 주문 상태가 마감됨으로 변경되는 문제를 수정합니다.
1. **ACSD-51036**: 동시 REST API 호출 중 경합 상태가 의 배송 상태 정보를 덮어쓰는 문제를 해결했습니다. [!UICONTROL Items Ordered] 테이블.
1. **ACSD-50858**: 카드 결제가 실패한 후 쿠폰이 사용된 것으로 잘못 표시되는 문제를 수정합니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
