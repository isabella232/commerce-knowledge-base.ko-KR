---
title: 일반적인 PHP 치명적인 오류 및 솔루션
description: 이 문서에서는 Adobe Commerce 로그와 문제가 표시된 솔루션을 통해 확인할 수 있는 몇 가지 일반적인 PHP 치명적 오류 빠른 예제를 나열합니다.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# 일반적인 PHP 치명적인 오류 및 솔루션

이 문서에서는 Adobe Commerce 로그와 문제가 표시된 솔루션을 통해 확인할 수 있는 몇 가지 일반적인 PHP 치명적 오류 빠른 예제를 나열합니다.

## 예

*&#39;PHP 치명적인 오류: 최대 실행 시간 60초 초과....&#39;*

## 솔루션

사용자 지정을 설정하여 최대 실행 시간을 업데이트할 수 있습니다 `max_execution_time` 의 값 `php.ini` 파일 및 재배포.

For example:

`max_execution_time = 120`

다음을 참조하십시오. [php.ini 설정 사용자 지정](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) 기사.

## 예

*&#39;PHP 치명적인 오류: 792723456바이트의 허용된 메모리 크기 소진&#39;* (이것은 단지 바이트 크기의 예입니다.)

## 솔루션

사용자 정의 `php.ini` 설정. 다음을 참조 [php.ini 설정 사용자 지정](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) 기사.

## 예

*&#39;PHP 경고: 알 수 없음: 스트림을 열지 못했습니다. 해당 파일 또는 디렉터리가 없습니다.&#39;*

## 솔루션

에서 Windows 스타일 끝을 제거하지 마십시오. `php.ini` 파일. Windows에서는 캐리지 리턴(ASCII 0x0d 또는 \r)과 CR/LF라고도 하는 줄바꿈(\n)의 조합으로 줄 끝이 종료됩니다.

## 예

*&#39;PHP에 심각한 오류: PDOException이 발견되지 않음: SQLSTATE\[HY000\] \[1040\] 연결이 너무 많음&#39;*

## 솔루션

MySQL 환경의 디스크 공간이 부족합니다. MySQL 환경에 더 많은 디스크 공간을 제공합니다.

## 예

*&#39;PHP 치명적인 오류: 발견되지 않은 TypeError: Magento 반환 값&#39;*

## 솔루션

다음 확인: `<root>/tmp` 디렉터리가 꽉 찼을 수 있습니다. 꽉 차면 디렉터리에 더 많은 공간을 제공합니다. 이 경우 파일을 다른 디렉토리로 이동하거나 삭제할 수 있습니다.

## 관련 읽기

개발자 설명서에서:

* [PHP 설정 오류](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [필수 PHP 설정](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [Redis 확인](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [Redis 구성](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [PHP 메모리 제한 오류](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [일반적인 문제에 대한 해결 방법 - 메모리 제한](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
