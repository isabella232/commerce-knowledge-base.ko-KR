---
title: Adobe Commerce 2.4.x에서 정확한 일치 검색이 작동하지 않음
description: 이 문서에서는 동일한 검색 문자열을 사용하는 스토어 전면 검색 결과가 Adobe Commerce 2.4.x와 Adobe Commerce 2.3.x의 차이가 있는 문제에 대한 설명을 제공합니다.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Adobe Commerce 2.4.x에서 정확한 일치 검색이 작동하지 않음

이 문서에서는 동일한 검색 문자열을 사용하는 스토어 전면 검색 결과가 Adobe Commerce 2.4.x와 Adobe Commerce 2.3.x의 차이가 있는 문제에 대한 설명을 제공합니다.

## 영향을 받는 제품 및 버전

- Adobe Commerce(모든 배포 방법) 2.4.x, 2.3.x
- 라이브 검색

## 문제

<u>사전 요구 사항:</u>

속성 값이 있는 제품이 있습니다. `Saga 1` 및 `Saga 16` Adobe Commerce 2.3 및 Adobe Commerce 2.4 상점 모두에서 사용할 수 있습니다.

<u>재현 단계:</u>

1. Adobe Commerce 2.3 기반 스토어 앞 스토어에서 를 입력합니다. *사가 호* 검색 필드에서 을(를) 클릭하고 **검색**.
1. 검색 결과에서는 속성 값이 있는 제품만 가져옵니다 `Saga 1`.
1. Adobe Commerce 2.4 기반 스토어 앞 스토어에서 를 입력합니다. *사가 호* 검색 필드에서 을(를) 클릭하고 **검색**.

<u>실제 결과:</u>

2.4의 검색 결과에는 속성 값이 있는 제품이 포함됩니다 `Saga 1` 및 `Saga 16`.

<u>예상 결과:</u>

2.4의 검색 결과는 2.3과 유사하며 속성 값이 있는 제품만 포함합니다 `Saga 1`.

## 원인

2.3.x에서 사용되는 Adobe Commerce 기본 검색 기능은 정확한 일치 검색 결과를 제공합니다. 라이브 검색 시 Adobe Commerce 2.4.x와 함께 릴리스된 설치할 수 있는 선택적 모듈인 라이브 검색은 다르게 구현되며 실제 결과는 모듈을 사용할 때 예상되는 비헤이비어입니다.

## 관련 읽기

[Live Search 설치](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) 사용 안내서에서 참조하십시오.

[라이브 검색](https://devdocs.magento.com/live-search/overview.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=Live%20Search) 개발자 설명서에서 확인할 수 있습니다.
