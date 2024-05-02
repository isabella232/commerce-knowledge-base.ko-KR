---
title: 설치하는 동안 예외 SessionHandler::read()
description: "이 문서에서는 Adobe Commerce 설치 중 **SessionHandler::read()** 오류에 대한 수정 사항을 제공합니다."
source-git-commit: 5cec04f8c4f80d34fc26b06eb929960ce21e2dc0
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# 설치하는 동안 예외 SessionHandler::read()

이 문서에서는 예외에 대한 수정 사항을 제공합니다 **SessionHandler::read()** Adobe Commerce 설치 중 오류가 발생했습니다.

## 문제

Adobe Commerce을 설치하는 마지막 단계에서 다음 예외가 표시됩니다.

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>이 오류는 2015년 9월 28일 이전 코드 버전에서만 발생합니다. 9월 29일 이상의 코드를 설치하는 경우 이 오류가 발생하지 않습니다. Redis용 구성 옵션에 대한 자세한 내용은 [Redis 구성](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) 개발자 설명서에서 확인할 수 있습니다. 명령줄 설치 프로그램을 사용하여 Redis 지정에 대한 자세한 내용은 [설치 주제](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-install.html) 또는 [배포 구성 항목](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp) 개발자 설명서에서 확인할 수 있습니다.

## 원인

다음 경우에 발생합니다. `session.save_handler` PHP 매개 변수가 `files` (예: `redis`, `memcached`등). 이 문제는 해결하기 위해 노력하고 있는 알려진 문제입니다.

## 솔루션:

* Adobe Commerce 코드를 업그레이드합니다. 을(를) 참조하십시오 [설치 안내서 > Adobe Commerce 소프트웨어 업데이트](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall.html#instgde-install-magento-update) 개발자 설명서에서 확인할 수 있습니다.
* 기존 코드에서 다음 해결 방법을 사용하십시오.

## 찾기 `php.ini` {#locate-php-ini}

찾기 `php.ini` 다음 명령을 입력합니다.

```php
php -i | grep "Loaded Configuration File"
```

일반적인 위치는 다음과 같습니다.

* 우분투: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## 해결 방법 {#workaround}

1. 을 사용하는 사용자로서 `root` 권한, 열기 `php.ini` 텍스트 편집기에서.
1. 찾기 `session.save_handler`
1. 다음 방법 중 하나로 설정합니다.
   * 주석을 달려면:

     ```php
     ;session.save_path = <path>
     ```

   * 파일 시스템 경로로 설정하려면 다음을 수행하십시오.

     ```php
     session.save_handler = files
     ```
