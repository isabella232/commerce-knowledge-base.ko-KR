---
title: GraphQL 요청에 대해 WAF를 우회하는 방법
description: 이 문서에서는 GraphQL 요청에 대해 WAF를 우회하는 방법을 설명합니다.
feature: GraphQL
source-git-commit: c35d4ba82fbe1657756e160a73fd575c736b4e1c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# GraphQL 요청에 대해 WAF를 우회하는 방법

이 문서에서는 다음과 같은 경우 GraphQL 요청에 WAF를 우회하는 방법을 설명합니다. [!DNL Fastly] WAF가 GraphQL 요청을 차단하고 있습니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce(모든 버전)

## 원인

GraphQL 요청의 고유한 특성으로 인해 의 요청을 거짓 양성 차단으로 트리거할 수 있는 반복되는 문자가 많이 있을 수 있습니다. [!DNL Fastly] 와프

## 솔루션

1. 를 통해 사용자 지정 코드 조각을 추가하여 이러한 요청에 대한 WAF를 우회합니다. [!DNL Fastly] Magento 모듈:

   유형: recv 우선 순위: 15 컨텐츠:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. 클릭 **[!UICONTROL Upload VCL to Fastly]**.

## 관련 읽기

* [WAF(Web Application Firewall)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) Commerce on Cloud Infrastructure 안내서에서 확인할 수 있습니다.
* [사용자 정의 VCL 시작하기](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) Commerce on Cloud Infrastructure 안내서에서 확인할 수 있습니다.

