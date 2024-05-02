---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: 이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 48563701-0fa0-4c88-943e-78b421b806b5
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool] (QPT) v1.1.39

이 하위 섹션에서는에서 사용할 수 있는 패치를 통해 해결된 문제에 대한 자세한 설명을 제공합니다. [!DNL Quality Patches Tool] (QPT) v1.1.39.

QPT v1.1.39에는 다음 패치가 포함됩니다.

1. **ACSD-53704**: 보상 포인트 만료 후 보상 포인트 잔고 내역이 잘못 계산되는 문제를 수정합니다.
1. **ACSD-53583**: 의 부분 색인 재지정 성능 개선 *범주 제품* 및 *제품 범주* 인덱서입니다.
1. **ACSD-54026**: 다음에 대한 잘못된 오류 메시지를 수정합니다. `updateCompanyRole` 권한이 없는 사용자에 대한 GraphQL 요청입니다.
1. **ACSD-54106**: 터키어 악센트 부호 문자에 대한 이름별 범주 제품 정렬이 잘못된 문제를 수정합니다.
1. **ACSD-52219**: 책갈피 보기 사이를 자주 전환할 때 관리 그리드 저장된 필터가 예상대로 작동하지 않는 문제를 수정했습니다.
1. **ACSD-54342**: 잘못된 오류 메시지를 수정합니다 *데이터 구조 오류: 값이 혼합되었습니다.* 유효한 데이터가 없는 CSV 파일을 가져올 때.
1. **ACSD-54660**: 새 입력 속성을 추가했습니다. *sort* GraphQL에서 고객 주문 정렬 기준 `sort_field` 및 `sort_direction`.
1. **ACSD-54776**: 이 선택되지 않은 문제를 해결합니다. *[!UICONTROL Use Default Value]* 및 기본값이 아닌 제품 필드 값은 두 번째 웹 사이트, 스토어 및 스토어 보기에 대해 저장되지 않습니다.
1. **ACSD-53998**: 가 발생하는 문제를 해결합니다. **[!UICONTROL Dynamic Block]** 를 기반으로 함 **[!UICONTROL Customer Segment]** 은 고객 계정에서 로그아웃한 후 올바르게 작동하지 않습니다.
1. **ACSD-53204**: 수정 사항 *제품을 저장할 수 없습니다.* 을(를) 사용하여 제품 갤러리에 이미지를 추가하도록 동시에 요청할 때 오류 발생 `rest/V1/products/<sku>/media` 엔드포인트.
1. **ACSD-47657**: AWS 자격 증명에 대한 캐싱 메커니즘을 추가했습니다. 이제 자격 증명 공급자는 Magento 캐시를 사용하여 EC2 구성을 위해 AWS에서 검색한 자격 증명을 캐시합니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
