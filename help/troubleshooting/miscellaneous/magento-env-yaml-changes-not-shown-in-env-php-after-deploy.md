---
title: 배포 후 env.php에 .magento.env.yaml 변경 사항이 표시되지 않음
description: 이 문서에서는 배포 후 .magento.env.yaml 파일의 변경 내용이 app/etc/env.php에 반영되지 않는 문제에 대한 해결 방법을 제공합니다.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# 배포 후 env.php에 .magento.env.yaml 변경 사항이 표시되지 않음

>[!NOTE]
>
>이 문제가 있는 경우 ece-tools 2002.1.5로 업그레이드하여 문제를 해결하십시오. 2002.1.5에는 각 배포에서 opcache를 재설정하는 기능이 있으므로 설정을 변경할 필요가 없습니다 `opcache.enable_cli=1`. 업그레이드하지 않으려면 솔루션에서 아래에 설명된 대로 해결 단계를 수행해야 합니다.

이 문서는에서 가 변경되는 문제에 대한 솔루션을 제공합니다. `.magento.env.yaml` 파일이 반영되지 않음 `app/etc/env.php` 배포 후.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce(모두 [지원되는 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## 문제

에서 변경된 사항 `.magento.env.yaml` 파일이 다음 항목에 영향을 주지 않음 `app/etc/env.php` 생성됨.

<u>재현 단계:</u>

에서 값 변경 `.magento.env.yaml` 을 누르고 서버에 푸시하면 현재 체크 아웃된 환경에 대한 구성(및 배포 설정)이 정의됩니다. 단계는 를 참조하십시오. [환경 변수 > 변수 배포](https://devdocs.magento.com/cloud/env/variables-deploy.html) 개발자 설명서에서 확인할 수 있습니다.

<u>예상 결과:</u>

에서 변경된 사항 `.magento.env.yaml` 파일이 다음에 영향을 줌 `app/etc/env.php` 생성됨.

<u>실제 결과:</u>

변경 사항은 다음에 영향을 주지 않습니다. `app/etc/env.php` 배포 후 변수.

## 원인

이 문제는 의 잘못된 값으로 인해 발생할 수 있습니다. `opcache.enable_cli` 의 매개 변수 `php.ini` 파일.

## 솔루션

1. 시스템이 다음 내용에 따라 구성되었는지 확인합니다. [Adobe Commerce 성능 모범 사례 > 소프트웨어 권장 사항](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html).
1. 다음을 확인: `opcache.enable_cli` 지시문 위치 `php.ini` 이(가) (으)로 설정됨 `0` 다음을 실행하여: `php -i | grep opcache.enable_cli`
1. 출력이 다음과 같은 경우 `opcache.enable_cli=1` , 편집 `php.ini` 프로젝트 루트 디렉터리의 파일 및 변경 `opcache.enable_cli=1` 끝 `opcache.enable_cli=0`
1. 프로젝트를 다시 배포합니다.

## 관련 읽기

* [Adobe Commerce용 클라우드 > 빌드 및 배포](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
