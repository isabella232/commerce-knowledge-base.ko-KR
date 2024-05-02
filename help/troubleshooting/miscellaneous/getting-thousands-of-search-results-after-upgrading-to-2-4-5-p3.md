---
title: 특정 제품을 찾을 때 수천 개의 결과 얻기
description: 이 문서에서는 특정 제품을 찾을 때 수천 개의 검색 결과를 얻는 문제에 대한 해결 방법을 제공합니다.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# 특정 제품을 찾을 때 수천 개의 결과 얻기

이 문서에서는 특정 제품을 찾을 때 수천 개의 검색 결과를 가져오는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 이 있는 모든 버전 Adobe Commerce [!DNL ElasticSearch] 설치됨

## 문제

특정 제품을 찾고 있습니다(예: *WSH12-32-빨강*)를 검색하면 유사한 제품이 많이 반환됩니다.

## 솔루션

의 전체 텍스트 검색 특성 [!DNL ElasticSearch] 는 정확한 일치가 아니라 관련성을 기반으로 합니다. 따라서 가장 관련성이 높은 일치(예: 정확히 일치하는 SKU)는 먼저 주문합니다.

그러나 검색어와 정확히 일치하는 검색 결과(정확히 일치)가 필요한 경우 검색 쿼리에 따옴표를 사용해야 합니다. 예를 들어 쿼리 *WSH12-32-빨강* 따옴표가 없으면 정확하게 일치하는 몇 가지 결과가 반환됩니다(제품: *SKU WSH12-32-Red*)이 결과의 맨 앞에 표시됩니다. 하지만 인용된 쿼리 *&quot;WSH12-32-Red&quot;* 는 하나의 정확한 일치 결과만 반환합니다.
