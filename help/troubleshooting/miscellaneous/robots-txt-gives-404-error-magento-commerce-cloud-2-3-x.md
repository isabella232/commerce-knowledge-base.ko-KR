---
title: robots.txt 클라우드 인프라에 404 오류 Adobe Commerce 제공
description: 이 문서에서는 'robots.txt' 파일에서 클라우드 인프라의 Adobe Commerce에 404 오류가 발생하는 경우에 대한 수정 사항을 제공합니다.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt 클라우드 인프라에 404 오류 Adobe Commerce 제공

이 문서에서는 다음과 같은 경우에 대한 수정 사항을 제공합니다 `robots.txt` 클라우드 인프라의 Adobe Commerce에서 파일에 404 오류가 발생합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce(모든 버전)

## 문제

다음 `robots.txt` 파일이 작동하지 않으며 Nginx 예외가 발생합니다. 다음 `robots.txt` 파일은 동적으로 &quot;즉시&quot; 생성됩니다. 다음 `robots.txt` 에서 파일에 액세스할 수 없음 `/robots.txt` Nginx에는 모든 리디렉션을 강제로 수행하는 다시 작성 규칙이 있으므로 URL `/robots.txt` 에 대한 요청 `/media/robots.txt` 존재하지 않는 파일입니다.

## 원인

일반적으로 Nginx가 제대로 구성되지 않은 경우 이 문제가 발생합니다.

## 솔루션

해결 방법은 리디렉션하는 Nginx 규칙을 비활성화하는 것입니다 `/robots.txt` 에 대한 요청 `/media/robots.txt` 파일. 셀프서비스가 활성화된 가맹점은 스스로 할 수 있고, 셀프서비스가 활성화되지 않은 가맹점은 지원 티켓을 만들 필요가 있다.

셀프 서비스를 활성화하지 않은 경우(또는 활성화 여부를 모를 경우), [Magento 지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 에서 Nginx 리디렉션 규칙 제거 요청 `/robots.txt` 에 대한 요청 `/media/robots.txt`.

셀프서비스를 활성화한 경우 ECE-Tools를 2002.0.12 이상으로 업그레이드하고 의 Nginx 리디렉션 규칙을 제거하십시오. `.magento.app.yaml` 파일. 다음을 의미할 수 있습니다. [사이트 맵 및 검색 엔진 로봇 추가](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) 자세한 내용은 개발자 설명서 를 참조하십시오.

## 관련 읽기

* [Fastly 수준에서 Magento Commerce Cloud을 위한 악성 트래픽을 차단하는 방법](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) 을 참조하십시오.
* [사이트 맵 및 검색 엔진 로봇 추가](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) 개발자 설명서에서 확인할 수 있습니다.
* [검색 엔진 로봇](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) 사용 안내서에서 참조하십시오.
