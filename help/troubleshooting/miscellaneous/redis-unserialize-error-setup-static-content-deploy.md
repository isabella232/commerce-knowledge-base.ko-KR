---
title: Redis unserialize 오류 `setup:static-content:deploy`
description: 이 문서에서는 'magento 설치' 실행 시 Redis unserialize 오류에 대한 수정 사항을 제공합니다:static-content:배포`.
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Redis unserialize 오류 `setup:static-content:deploy`

이 문서에서는 실행 시 Redis unserialize 오류 수정 사항을 제공합니다. `magento setup:static-content:deploy`.

실행 중 `magento setup:static-content:deploy` 는 Redis 오류를 발생시킵니다.

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

이 문제는 Redis 연결에 대한 병렬 간섭 프로세스로 인해 발생합니다.

해결하려면 다음을 실행합니다. `setup:static-content:deploy` 다음 환경 변수를 설정하여 단일 스레드 모드로 전환할 수 있습니다.

```
STATIC_CONTENT_THREADS =1
```

또는 `setup:static-content:deploy` 명령 뒤에 `-j 1` (또는 `--jobs=1` ) 인수.

다중 스레딩을 비활성화하면 정적 에셋을 배포하는 프로세스가 느려집니다.

## 영향을 받는 버전

* Adobe Commerce 온-프레미스: 2.1.2 이상
* cloud infrastructure 2.1.2 이상 버전의 Adobe Commerce
* Redis, 모든 버전

## 문제

실행 `setup:static-content:deploy` 이 명령으로 인해 Redis 오류가 발생합니다.

```php
)
[2017-06-02 19:57:59] Command:php ./bin/magento setup:static-content:deploy --jobs=3  en_US

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[CredisException]
read error on connection

[RedisException]
read error on connection

.....

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[RuntimeException]
Command php ./bin/magento setup:static-content:deploy --jobs=3  en_US  returned code 3
```

## 원인

이 문제는 Redis 연결의 병렬 간섭 프로세스로 인해 발생합니다.

여기, 의 프로세스입니다 `App/Config/Type/System.php` 다음에 대한 응답이 필요합니다: `system_defaultweb`에 대한 응답을 수신함 `system_cache_exists` 그것은 다른 과정에 의해 만들어졌다. 자세한 설명은 을 참조하십시오. [제이슨 우즈의 게시물](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## 솔루션

병렬 처리 수 비활성화 및 실행 `setup:static-content:deploy` 다음 환경 변수를 설정하여 단일 스레드 모드로 전환할 수 있습니다.

```
STATIC_CONTENT_THREADS =1
```

다음을 실행할 수도 있습니다. `setup:static-content:deploy` 명령 뒤에 `-j 1` (또는 `--jobs=1`) 인수.

>[!NOTE]
>
>단일 스레드 모드에서 정적 콘텐츠 배포 프로세스는 4배 더 걸릴 수 있습니다.

## 추가 정보

개발자 설명서에서:

* [Redis 구성](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [명령줄 업그레이드](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)
