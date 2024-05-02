---
title: robots.txt가 업데이트되지 않거나 기본 설정이 표시됨
description: 이 문서에서는 예를 들어 [Adobe Commerce robots.txt 우수 사례](https://support.magento.com/hc/en-us/articles/360048754931)에 따라 'robots.txt'를 올바르게 구성했지만 'robots.txt'가 업데이트되지 않거나 기본 설정이 표시되는 경우를 위한 솔루션을 제공합니다.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt가 업데이트되지 않거나 기본 설정이 표시됨

이 문서에서는 을(를) 구성한 경우의 솔루션을 제공합니다 `robots.txt` 올바르게, 예: [Adobe Commerce robots.txt 우수 사례](https://support.magento.com/hc/en-us/articles/360048754931) 하지만 `robots.txt` 이(가) 업데이트되지 않거나 기본 설정을 표시합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.3.x, 2.4.x

## 문제

기본값을 변경할 수 없음 `robots.txt` 설정.

<u>재현 단계:</u>

1. 관리 패널에 액세스합니다.
1. 콘텐츠 추가 **콘텐츠** > 디자인 > **구성** > **의 사용자 정의 지침 편집`robots.txt`** &quot;hello&quot; 텍스트와 같은 파일을 저장하고 변경 내용을 저장합니다.
1. 다음 방문: `robots.txt` url.

<u>예상 결과:</u>
`robots.txt` 에 저장된 텍스트가 있습니다.

<u>실제 결과:</u>

`robots.txt` 파일이 변경되지 않습니다.

## 원인

검색 엔진에 의한 색인화가 해제되었습니다.

## 솔루션

검색 엔진별 색인화를 활성화합니다. 다음을 참조하십시오 [검색 엔진별 색인화 구성](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html#configure-indexing-by-search-engine) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

* [사이트 맵 및 검색 엔진 로봇 추가](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) 개발자 설명서에서 확인할 수 있습니다.
