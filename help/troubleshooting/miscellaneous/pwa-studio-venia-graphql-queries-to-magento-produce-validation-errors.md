---
title: "PWA Studio: Adobe Commerce에 대한 Venia GraphQL 쿼리에서 유효성 검사 오류가 발생했습니다."
description: 이 문서에서는 Adobe Commerce 인스턴스에 대한 Venia storefront GraphQL 쿼리가 유효성 검사 오류를 생성하는 문제를 해결하는 방법에 대한 권장 사항을 제공합니다.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio: Adobe Commerce에 대한 Venia GraphQL 쿼리에서 유효성 검사 오류가 발생했습니다.

이 문서에서는 Adobe Commerce 인스턴스에 대한 Venia storefront GraphQL 쿼리가 유효성 검사 오류를 생성하는 문제를 해결하는 방법에 대한 권장 사항을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.2.x, 2.3.x
* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x
* Adobe Commerce용 프로젝트 PWA Studio

## 문제

Adobe Commerce 온프레미스 또는 클라우드 인프라의 Adobe Commerce에 대한 Venia GraphQL 쿼리는 유효성 검사 오류를 생성합니다.

## 원인

문제를 일으키는 원인 중 하나는 Venia 및 해당 GraphQL 쿼리가 연결된 Adobe Commerce 인스턴스의 스키마와 동기화되지 않았기 때문일 수 있습니다.

## 솔루션

쿼리가 최신 상태인지 테스트하려면 프로젝트 루트에서 다음 명령을 실행합니다.

```bash
yarn run validate-queries
```

호환성 보고서를 표시합니다. 호환되지 않는 경우 PWA Studio 또는 Adobe Commerce 인스턴스를 업그레이드해야 합니다. 다음 확인: [Adobe Commerce 호환성 매트릭스](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) 필요한 버전을 정확히 확인합니다.

업그레이드 방법에 대한 지침은 다음 설명서를 참조하십시오.

* PWA Studio 업그레이드의 경우 의 &quot;이전 버전에서 업그레이드&quot; 섹션을 검색합니다. [PWA 릴리스 노트](https://github.com/magento/pwa-studio/releases/) 로 업그레이드해야 하는 버전입니다.
* [클라우드 인프라 버전의 Adobe Commerce 업그레이드](https://devdocs.magento.com/cloud/project/project-upgrade.html) 개발자 설명서에서
* [Adobe Commerce 온-프레미스 업그레이드(&quot;작성기 create-project&quot; 또는 아카이브를 사용하여 설치됨)](https://devdocs.magento.com/guides/v2.3/comp-mgr/cli/cli-upgrade.html) 개발자 설명서에서
* [Adobe Commerce 온-프레미스 업그레이드(Adobe Commerce 저장소 복제에 의해 설치됨)](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/dev_update-magento.html) 개발자 설명서에서

## 관련 읽기

* [PWA Studio: 컴파일을 시작하기 전에 Webpack이 중단됨](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) 지원 기술 자료
* [PWA Studio: 개발자 모드를 실행할 때 유효성 검사 오류 발생](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) 지원 기술 자료
* [PWA Studio: 브라우저에 &quot;프록시 대상 불가&quot; 오류 표시](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) 지원 기술 자료
* [PWA Studio을 사용할 수 있도록 NPM 구성](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) 지원 기술 자료
* [Adobe Commerce 설명서 PWA](https://magento.github.io/pwa-studio/)
