---
title: 잘못 구성되거나 누락되어 크론이 중지됨 [!DNL OpCache] 설정
description: 이 문서에서는 잘못 구성되거나 누락되어 크론이 작동하지 않는 경우에 대한 해결 방법을 제공합니다 [!DNL OpCache] 설정.
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# 잘못 구성되거나 누락되어 Cron이 중지됨 [!DNL OpCache] 설정

이 문서에서는 누락되거나 잘못 구성된 이유로 cron 이 작업을 중단하는 경우에 대한 해결 방법을 제공합니다 [!DNL OpCache] 설정.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## 문제

크론이 작동을 멈췄다.

## 원인

다음 [!DNL OpCache] 모듈이 를 도입한 최신 버전으로 업데이트되었습니다. [!DNL GraphQL] 을(를) 재작성하는 플러그인 `env.php` 런타임 시 및 가 cron 설정을 재정의할 수 있으며, 이로 인해 문제가 발생했을 수 있습니다. 다음 [!DNL OpCache] 의 문제를 방지하기 위해 구성을 업데이트해야 합니다. `env.php file`, 그리고 이 문제는 다음 위치에서 해결되었습니다. [버전 2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) / [!DNL ECE Tools] 패키지.

## 솔루션

옵션 1: 명령줄 도구에서 다음을 실행합니다.

```bash
bin/magento cron:run
```

cron 이 비활성화되어 있다는 메시지가 표시될 수 있습니다.

옵션 2: `app/etc/env.php` 파일 - 아래가 표시되면 cron이 수동으로 비활성화되었거나, 실패한 배포로 인해 다시 활성화되지 않았거나, 문제가 [!DNL OpCache] 설정.

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. cron 이 비활성화되어 있으면 이 명령을 실행하여 cron 을 다시 활성화하십시오. `vendor/bin/ece-tools cron:enable`
1. 의 최신 버전을 사용하고 있는지 확인하십시오. [!DNL ECE Tools]. 그렇지 않은 경우 업그레이드하거나 항목 3으로 건너뜁니다. 기존 버전을 확인하려면 다음 명령을 실행합니다.
   `composer show magento/ece-tools`
1. 의 최신 버전을 사용하고 있는 경우 [!DNL ECE Tools], 이(가) 있는지 확인 `op-exclude.txt` 파일. 이렇게 하려면 이 명령을 실행합니다.
   `ls op-exclude.txt`.
이 파일이 없으면 리포지토리에 https://github.com/magento/magento-cloud/blob/master/op-exclude.txt을 추가한 다음 변경 내용을 커밋하고 다시 배포합니다.
1. 업그레이드할 필요 없음 [!DNL ECE Tools]를 클릭하여 리포지토리에서 https://github.com/magento/magento-cloud/blob/master/op-exclude.txt을 추가/수정한 다음 변경 사항을 커밋하고 다시 배포할 수도 있습니다.

## 관련 읽기

* [Cron 준비 확인 문제](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Crons 속성](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [Cron 작업이 &quot;실행 중&quot; 상태로 중단됨](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
