---
title: 이유 확인 방법 [!DNL cron] 비활성화됨
description: 이 문서에서는 클라우드 인프라 제품에서 Adobe Commerce의 cron 관련 문제에 대한 문제 해결 솔루션을 제공합니다.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# 이유 확인 방법 [!DNL cron] 비활성화됨

이 문서에서는 문제 해결 솔루션을 제공합니다. [!DNL cron] Adobe Commerce on cloud infrastructure 제품.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전

## 문제

## 다음은 의 증상입니다. [!DNL cron] 문제:

이(가) [!DNL cron] 실행 중이 아닙니다.
예를 들어, 다음 줄을 `app/etc/env.php` 파일:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

배열이 비어 있으면 [!DNL cron] 은(는) **활성화됨**:

```'cron' =>
  array (
  ),
```

## 원인

다음과 같은 몇 가지 이유가 있습니다 [!DNL cron] 은(는) 현재 활성화되지 않았습니다.

1. 다음 [!DNL cron] 누락으로 인해 비활성화되었습니다. [!DNL OpCache] 설정.
1. 인프라 팀이 다음을 비활성화했습니다. [!DNL cron]로 인해 사이트의 성능이 저하되었거나 다운이 발생했기 때문입니다.
1. 다음 [!DNL cron] 배포가 실패하여 다시 활성화되지 않았습니다.

문제에 대한 해결 방법은 다음 섹션 중 하나를 참조하십시오.

## 솔루션

### 누락을 위한 솔루션 [!DNL OpCache] 설정 {#solution-missed-opcache-settings}

다음을 참조하십시오 [[!DNL Cron] 잘못 구성되거나 누락되어 중지됨 [!DNL OpCache] 설정](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) Commerce 기술 자료에서.

### 인프라 팀이 비활성화한 솔루션 {#solution-disabled-by-infrastructure-team}

1. 사이트가 다운되었거나 응답하지 않는 이전 지원 티켓을 확인합니다.
1. 그런 다음 인프라 팀이 이를 비활성화했음을 표시했는지 확인합니다.
1. 인프라 팀이 제기한 문제/문제를 해결했는지 확인합니다.
1. 제출 [지원 요청](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) 다시 활성화하기 위해 추가 지원이 필요한 경우 [!DNL cron] 인프라 팀이 지적한 문제를 어떻게 해결했는지 설명합니다.

### 배포용 솔루션 실패 {#solution-deployment-failed}

배포 로그를 확인합니다.

* [로그 보기 및 관리](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) Commerce on Cloud Infrastructure Guide를 참조하십시오.
* [Cloud UI에 이 있는 경우 배포 로그 확인 *`log snipped`* 오류](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) Commerce 기술 자료에서.

1. 배포 도중 실패한 경우 `setup:upgrade` 단계, [!DNL cron] 다시 활성화되지 않습니다.
예를 들어 배포 로그에 다음 줄이 표시됩니다.

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. 그렇지 않으면 다른 단계에서 배포가 실패했을 수 있습니다. 배포 로그를 확인하고 두 행이 모두 표시되는지 확인합니다(아래 예). 로그에 이와 유사한 두 행이 모두 표시되지 않으면 다음을 의미합니다. [!DNL cron] 이(가) 다시 활성화되지 않았습니다.

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**제출 [지원 요청](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) 추가 지원이 필요한 경우**
