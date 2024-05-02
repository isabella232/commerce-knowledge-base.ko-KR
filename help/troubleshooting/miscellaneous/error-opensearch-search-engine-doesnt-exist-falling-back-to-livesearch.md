---
title: 오류 [!DNL opensearch] 검색 엔진이 존재하지 않습니다. 으로 폴백 [!DNL livesearch].
description: 이 문서에서는 '오류' 오류가 표시되는 문제에 대한 해결 방법을 제공합니다. [!DNL opensearch] 검색 엔진이 존재하지 않습니다. 으로 폴백 [!DNL livesearch]클라우드 인프라의 Adobe Commerce에서 .`.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# 오류 [!DNL opensearch] 검색 엔진이 존재하지 않습니다. 으로 폴백 [!DNL livesearch].

이 문서에서는 오류가 표시되는 문제에 대한 해결 방법을 제공합니다. *오류: [!DNL opensearch] 검색 엔진이 존재하지 않습니다. 으로 폴백 [!DNL livesearch].* Adobe Commerce on cloud infrastructure의 [!DNL Live Search] 를 사용합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전
* [!DNL Live Search] 이(가) 설치되어 사용 중입니다

## 문제

다음 메시지는 로그에 표시되며 다음에서 확인할 수 있습니다. [!DNL New Relic]):
*오류: [!DNL opensearch] 검색 엔진이 존재하지 않습니다. 으로 폴백 [!DNL livesearch].*

## 솔루션

1. 수정 `.magento.env.yaml` 파일.
1. 다음 줄을 찾습니다.

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. 이 줄이 없으면 다음 줄에 추가합니다. `.magento.env.yaml` 파일.
1. 이 줄이 있으면, **엔진 수정** 출처: *[!DNL opensearch]* 끝 *[!DNL livesearch]*.
1. 변경 사항을 커밋한 다음 재배포합니다.

## 관련 읽기

* [설치 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) 라이브 검색 안내서에서
