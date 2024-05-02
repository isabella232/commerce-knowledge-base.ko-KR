---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.0.13'
description: 이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.0.13.
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.13 개요

이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.0.13.

QPT v1.0.13에는 다음 패치가 포함됩니다.

1. **MCP-**: 대형 프로필에 대한 카테고리 제품 및 스톡 인덱서의 색인 지정 시간이 개선되었습니다.
1. **MDVA-13203**: 이(가) 발생하는 문제를 수정합니다. *무결성 제한 위반 search_tmp_ 테이블* 전체 색인 재지정 후 오류가 나타납니다.
1. **MDVA-19391**: 다음의 문제를 해결합니다. `analytics_collect_data` 의 NULL 설명 레코드로 인해 오류가 발생합니다. `catalog_category_entity_text` 테이블.
1. **MDVA-20376**: 와 관련된 문제가 해결되었습니다. *customerId = 1인 엔티티가 없음* 에 오류 발생 `exception.log` 주문 배치 후 로그인한 고객의 경우
1. **MDVA-22150**: 장바구니에서 구성 가능한 제품을 사용하고 쿠폰이 적용된 고객이 관리에서 구성 가능한 제품을 사용하지 않도록 설정한 경우 로그인할 수 없는 문제가 수정되었습니다.
1. **MDVA-23426**: Adobe Commerce에서 보낸 알림 이메일에 첨부 파일로 추가되는 내용이 있는 빈 본문이 포함되어 있는 문제를 수정합니다.
1. **MDVA-23764**: 의 버그를 수정합니다. `JsFooterPlugin.php` 동적 블록의 표시에 영향을 줍니다.
1. **MDVA-30858**: 의 문제를 수정합니다 [!DNL PayPal] 다음에서 결제 보고서를 사용할 수 없음: **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** 예상대로 해결되었습니다.
1. **MDVA-32545**: 관리자로부터 주문을 생성할 때 송장이 자동으로 전송되지 않는 문제를 수정합니다.
1. **MDVA-32714**: GraphQL 제품 쿼리에서 고객 그룹 가격이 작동하지 않는 문제를 수정합니다.
1. **MDVA-33106**: cron 후에 다시 일정이 잡힌 제품 변경 사항이 지워지는 문제를 수정합니다 `run` 명령이 실행됩니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
