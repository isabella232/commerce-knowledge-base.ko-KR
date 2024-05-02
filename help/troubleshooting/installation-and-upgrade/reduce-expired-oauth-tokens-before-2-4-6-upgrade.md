---
title: 2.4.6 업그레이드 전에 만료된 'oauth_tokens' 감소
description: 이 문서에서는 'oauth_token' 테이블에 많은 'oauth_tokens'가 표시되던 문제에 대한 해결 방법을 제공합니다. 이러한 경우 버전 2.4.6으로 업그레이드하는 데 오랜 시간이 걸릴 수 있습니다. CleanExpiredTokens.php를 사용하여 'oauth_token' 테이블을 줄이는 것이 좋습니다.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# 만료 날짜 줄이기 `oauth_tokens` 2.4.6 업그레이드 전

이 문서에서는 이(가) 많이 표시되는 문제에 대한 해결 방법을 제공합니다. `oauth_tokens` (으)로 `oauth_token` 테이블 - 버전 2.4.6으로 업그레이드하는 데 오랜 지연이 발생할 수 있습니다. 다음을 줄이는 것이 좋습니다. `oauth_token` 표를 사용한 [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] 만료된 토큰을 삭제하는 작업입니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.0 - 2.4.6, 모든 배포 방법

## 문제

많은 수가 있는 경우 `oauth_tokens` (으)로 `oauth_token` 이 경우 버전 2.4.6으로 업그레이드하는 데 오랜 지연이 생길 수 있습니다.

업그레이드 프로세스에는 추가 보안 계층을 위해 이러한 토큰을 암호화하는 작업이 포함되며 한 번에 100개의 레코드만 수행됩니다. 토큰이 많은 경우 몇 시간이 걸릴 수 있습니다.

많은 수의 `oauth_tokens` (으)로 `oauth_token` 테이블을 사용하면 버전 2.4.6으로 업그레이드하는 데 오랜 지연이 발생하지 않습니다.

## 솔루션

업그레이드를 시작하기 전에 먼저 [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] 작업이 실행 중입니다. 의 크기를 줄입니다 `oauth_token` 만료된 테이블을 삭제하여 테이블 `oauth_tokens` 토큰으로 설정되며, 기본적으로 이미 활성화되어 있어야 합니다.

수동으로 트리거하려면 [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] 작업, 실행:
```bin/magento cron:run --group=default```

## 관련 읽기

* [서비스 > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) Commerce 구성 참조 안내서에서 참조할 수 있습니다.
* [Authentication 안내서](https://developer.adobe.com/developer-console/docs/guides/authentication/) Adobe Developer 안내서에서 확인할 수 있습니다.
