---
title: '''[!DNL SendGrid] Adobe Commerce Cloud에 대한 파일 제한'
description: 이 문서에서는 의 해결 방법을 제공합니다.  [!DNL SendGrid] 클라우드 인프라의 Adobe Commerce 제한 사항.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# [!DNL SendGrid] Adobe Commerce Cloud 제한 사항

이 문서에서는 몇 가지 해결 방법을 제공합니다. [!DNL SendGrid] 클라우드 인프라의 Adobe Commerce 제한 사항.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## 문제

이메일에 첨부 파일을 크게 보내고 다음 로그 오류를 확인하려고 합니다.

위치 `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

위치 `/var/log/exception.log`

프로덕션:

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

스테이징:

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

스테이징2:

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## 원인

[!DNL SendGrid] 에는 이메일의 시스템 크기가 30Mb로 제한됩니다. 10Mb를 초과하는 첨부 파일은 사용하지 않는 것이 좋습니다. 다음을 참조하십시오 [첨부 파일 보내기](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) 자세한 내용은 SendGrid 설명서 를 참조하십시오.

## 해결 방법

* 6Mb 또는 10Mb 이상의 첨부 파일을 사용하지 마십시오.
* Adobe Commerce 인스턴스에서 원격 SMTP 서버를 사용하는 것이 좋습니다. 단계는 를 참조하십시오. [이메일 커뮤니케이션 구성](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html) 관리 시스템 안내서에서 확인할 수 있습니다.
* 파일을 모듈 내에 저장할 수 있도록 서버를 다시 구성한 다음 이메일의 파일에 대한 링크를 첨부합니다.

## 관련 읽기

* [[!DNL SendGrid] 이메일 서비스](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html) Commerce on Cloud Infrastructure Guide를 참조하십시오.
