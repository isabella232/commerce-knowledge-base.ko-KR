---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.0.20'
description: 이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.0.20.
exl-id: 13ed85f9-4ecb-467f-9ed0-ceec4ac200db
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.20 개요

이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.0.20.

QPT v1.0.20에는 다음 패치가 포함됩니다.

1. **MC-41359**: 잘못된 SameSite 쿠키 매개 변수 설정의 문제를 수정합니다.
1. **MDVA-11189**: CSV 파일을 가져와서 제품 재고, 의 행을 업데이트할 때 발생하는 문제를 수정합니다. `cataloginventory_stock` 테이블이 삭제됩니다.
1. **MDVA-15546**: 주문 생성 후 의 문제를 해결합니다. *열 entity_id where 절이 모호합니다.* 예외 로그에 오류가 표시됩니다.
1. **MDVA-19640**: 다음의 문제를 해결합니다. [!DNL Advanced Reporting] 은(는) 데이터를 표시하지 않습니다.
1. **MDVA-21095**: 쿼리 시 문제를 해결합니다 `INSERT INTO search_tmp` 대량 속성 값을 업데이트한 후에는 종료되지 않습니다.
1. **MDVA-22026**: 외부 URL의 이미지를 포함하여 CSV 파일에서 제품을 가져오지 못하는 문제를 해결합니다.
1. **MDVA-22383**: 제품 저장에 시간이 오래 걸리고 페이지가 중단되는 문제를 해결합니다.
1. **MDVA-23845**: JavaScript 축소가 활성화된 후 이메일 템플릿을 미리 볼 수 없는 문제를 수정합니다.
1. **MDVA-26639**: 새 주문 확인 이메일 템플릿이 만들어지면 주문 메일에서 주문 항목이 누락되는 문제를 수정합니다.
1. **MDVA-33168**: API를 통해 제품 속성을 업데이트할 때 다른 모든 속성이 빈 값으로 변경되는 문제를 수정합니다.
1. **MDVA-36170**: 카테고리 캐시 태그를 사용하여 GraphQL 쿼리가 캐싱하지 않는 문제를 해결합니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
