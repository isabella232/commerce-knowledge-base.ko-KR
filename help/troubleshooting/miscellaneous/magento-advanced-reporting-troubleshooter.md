---
title: Adobe Commerce용 고급 보고 문제 해결사
description: Adobe Commerce의 고급 보고 문제는 이 문제 해결사 도구를 사용하여 해결할 수 있습니다. 여기에는 데이터를 표시하지 않는 고급 보고와 404 오류가 포함됩니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 84b4ca4c4144381f0b404d2eae6684e7b21755df
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Adobe Commerce용 고급 보고 문제 해결사

Adobe Commerce의 고급 보고 문제는 이 문제 해결사 도구를 사용하여 해결할 수 있습니다. 여기에는 데이터를 표시하지 않는 고급 보고와 404 오류가 포함됩니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다.

## 1단계 - 사이트가 고급 보고 요구 사항을 충족하는지 확인 {#step-1}

+++**웹 사이트가 고급 보고 요구 사항을 충족합니까?**

고급 보고를 사용할 때 404 오류 페이지가 표시됩니다. 웹 사이트 충족 여부 [고급 보고 요구 사항](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements)?

a. 예 - 진행합니다. [2단계](#step-2).\
b. 아니오 - 의 단계에 따라 사이트에 대한 고급 보고 요구 사항을 완료합니다. [고급 보고 요구 사항](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements). 그런 다음 로 진행합니다. [2단계](#step-2).

+++

## 2단계 - 여러 기본 통화로 주문이 있습니까? {#step-2}

+++**여러 기본 통화가 사용됩니까?**

주문 및 구성에서 여러 기본 통화가 사용됩니까? 이 SQL 명령을 실행하여 현재 구성을 가져옵니다. `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. 예 - 쿼리에서 반환된 행이 여러 개인 경우 한 통화만 지원하므로 고급 보고를 사용할 수 없습니다.\
b. NO - 출력에 하나의 통화만 표시됩니다. 예: `USD`. 주문에서 여러 기본 통화가 사용된 적이 있습니까? 다음 SQL 명령을 실행하여 내역 주문 데이터를 가져옵니다.\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**참고: 이 명령을 사용하려면 전체 테이블을 스캔해야 하므로 레코드 수가 많은 테이블의 경우 쿼리가 실행되는 동안 성능에 영향을 줄 수 있습니다** 기록 주문 데이터를 가져옵니다.
여러 기본 통화가 사용된 경우 하나의 통화만 지원되므로 고급 보고를 사용할 수 없습니다. 출력에 하나의 통화만 표시되면 다음으로 진행합니다. [3단계](#step-3).

+++

## 3단계 - 분할 데이터베이스가 사용 중인지 확인 {#step-3}

+++**데이터베이스 분할 솔루션을 사용하고 있습니까?**

을(를) 사용 중입니다. [데이터베이스 분할 솔루션](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html)?

a. 예 - 패치 사용 **MDVA-26831** 위치: [분할 데이터베이스 솔루션의 고급 보고 404 오류](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-404-error-on-split-database-solution.md) 캐시를 지웁니다. 작업이 다시 실행될 때까지 24시간 기다린 후 다시 시도하십시오.\
b. 아니요 - 진행합니다. [4단계](#step-4).

+++

## 4단계 - 고급 보고 활성화 확인 {#step-4}

+++**고급 보고가 활성화되어 있습니까?**

확인 **관리자** > **스토어** > **설정** > **구성** > **일반** > **고급**. 자세한 단계는 을 참조하십시오. [고급 보고: 고급 보고 활성화](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting).

a. 예 - 진행합니다. [5단계](#step-5).\
b. 아니요 - [고급 보고 활성화](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) 저장하고 Adobe Commerce 및 고급 보고가 동기화되도록 24시간 동안 기다립니다. 이제 데이터가 로드되는지 확인합니다. 만약 당신이 문제를 해결했다면. 진행되지 않는 경우 [5단계](#step-5).

+++

## 5단계 - 토큰 확인 {#step-5}

+++**토큰 있어요?**

다음 쿼리를 실행하여 토큰이 있는지 확인하십시오. `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` 토큰 있어요?

a. 예 - 진행합니다. [7단계](#step-7).\
b. NO - 토큰 값이 NULL이거나 데이터베이스에 레코드가 없는 경우 [6단계](#step-6).

+++

## 6단계 - 행 사용 {#step-6}

+++**쿼리가 행을 반환합니까?**

이 쿼리를 실행하여 플래그 테이블의 카운터 값 확인: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` 쿼리가 행을 반환합니까?

a. 예 - 다음 단계를 수행합니다. 1. 아래 쿼리를 실행합니다.\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [고급 보고 모듈 비활성화 및 활성화](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) 설정 및 [토큰 재인증](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
3\. Adobe Commerce 및 고급 보고가 동기화할 때까지 24시간 대기합니다. 여전히 고급 보고에서 데이터를 볼 수 없는 경우 [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. 아니오 - 쿼리가 아무 것도 반환하지 않으면 다음 단계를 수행합니다. 1. [고급 보고 모듈 비활성화 및 활성화](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) 설정 및 [토큰 재인증](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
2\. Adobe Commerce 및 고급 보고가 동기화할 때까지 24시간 대기합니다. 여전히 고급 보고에서 데이터를 볼 수 없는 경우 [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 7단계 - 다음 위치에서 레코드 확인 `cron_schedule` 표 {#step-7}

+++**다음 항목에 레코드가 있습니까? `cron_schedule` 테이블?**

해당 작업 확인 `analytics_collect_data` 이(가) 이 쿼리를 실행하여 실행되었습니다. `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. 예 - 레코드와 **상태** 열 메시지 _누락_, 이 KB 문서의 패치 사용 [자체 cron 그룹에서 실행되도록 고급 보고 업데이트](/help/troubleshooting/known-issues-patches-attached/update-advanced-reporting-to-run-on-its-own-cron-group.md).\
b. 예 - 레코드와 **상태** 열 메시지 _성공_, 다음으로 진행 [9단계](#step-9).\
c. 예 - 레코드와 **상태** 열 메시지 _오류_, 다음으로 진행 [8단계.](#step-8)\
d. NO - 레코드가 없는 경우 다음 단계로 진행합니다. [8단계](#step-8).

+++

## 8단계 - 작업 확인 `support_report.log` {#step-8}

+++**작업이 로그인되었습니다. `support_report.log`?**

다음 명령을 실행합니다. `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. 예 - 질의 출력이 성공적인 작업을 나타내는 경우, 예를 들어 `Cron Job analytics_collect_data is successfully finished` 다음으로 진행 [9단계](#step-9).\
b. 아니요 - 로그에 레코드가 없으면 [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. 예 - 레코드가 있지만 오류가 있는 경우 [10단계](#step-10).

+++

## 9단계 - 확인 `data.tgz` 파일 {#step-9}

+++**파일이 `data.tgz` 시스템에 있고 액세스 로그에 레코드가 있습니까?**

파일을 확인하려면 `data.tgz` 존재함, 명령 실행:

```
ls -ltr pub/media/analytics/<there should be a directory with hash name>/
```

access.logs에 레코드가 있는지 확인하려면 명령을 실행합니다.

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a. 예 - 파일이 `data.tgz` 이(가) 있고 액세스 로그에 레코드가 있지만 404 오류가 여전히 있으므로 다음을 수행해야 합니다. [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. 아니요 - 진행합니다. [10단계](#step-10).

+++

## 10단계 - 오류 메시지 확인 {#step-10}

+++**cron 작업에서 오류 메시지가 표시됩니까?**

예: `core_config_data` 오류를 표시한 표 *&quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0 파일을 삭제할 수 없습니다.*. 경고!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0?lang=en): 해당 파일 또는 디렉터리가 없습니다.*

a. 예 - ACSD-50165 패치 사용 [파일을 삭제할 수 없습니다. 경고!unlink: 관리자의 파일 또는 디렉터리 오류가 없습니다.](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md), 작업이 다시 실행될 때까지 24시간 기다린 후 다시 시도하십시오.\
b. 아니요 - 진행합니다. [11단계](#step-11).

+++

## 11단계 - 페이지 빌더 오류가 있는지 확인 {#step-11}

+++**페이지 빌더로 인해 오류가 발생합니까?**

예: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. 예 - MDVA-19391 패치 사용 [Adobe Commerce의 일반적인 고급 보고 cron 작업 오류](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-cron-job-errors-magento-commerce.md), 작업이 다시 실행될 때까지 24시간 기다린 후 다시 시도하십시오.\
b. 아니요 - [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[1단계로 돌아가기](#step-1)
