---
title: Adobe Commerce의 max_allowed_packet 관련 데이터베이스 오류
description: 이 문서에서는 'var/log/exception.log'에서 대량의 제품을 가져오거나 서버에서 기본값인 16MB보다 큰 'max_allowed_packet'에 설정된 보다 큰 패킷을 처리하도록 하는 작업을 수행할 때 발생할 수 있는 데이터베이스 연결 오류에 대한 해결 방법을 제공합니다.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Adobe Commerce의 max_allowed_packet 관련 데이터베이스 오류

이 문서에서는 의 데이터베이스 연결 오류에 대한 솔루션을 제공합니다. `var/log/exception.log` 많은 수의 제품을 가져오거나 서버에서 설정된 것보다 큰 패킷을 처리하도록 하는 다른 작업을 수행할 때 발생할 수 있습니다 `max_allowed_packet` 기본값인 16MB보다 큽니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스, 모두 [지원되는 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 문제

MySQL 클라이언트 또는 [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) 서버가 다음보다 큰 패킷을 수신함: [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) 바이트, 발행 [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) 오류(다음에서 볼 수 있음) `exception.log`) 연결을 닫습니다. 일부 클라이언트에서는 *쿼리하는 동안 MySQL 서버에 대한 연결이 끊어졌습니다.* 통신 패킷이 너무 큰 경우 오류가 발생합니다.

<u>재현 단계</u>

다양한 작업에서 이 문제를 발생시킬 수 있습니다. 여기에는 많은 수의 제품을 Adobe Commerce으로 가져오려고 시도하거나 너무 많은 데이터를 다시 보내는 트랜잭션 쿼리가 포함될 수 있습니다. 그 결과는에서 데이터베이스 연결 오류입니다. `var/log/exception.log` 및 제품을 성공적으로 가져오지 못하는 것과 같은 기타 문제.

## 원인

MySQL의 기본값 16MB `max_allowed_packets` 설정이 사용자의 요구 사항에 비해 충분히 크지 않습니다.

## 솔루션

1. 개별 행이 현재 행을 초과하는 쿼리 식별 `max_allowed_packet` 제한. 이러한 쿼리는 반환되는 데이터의 양을 줄이기 위해 다시 작성해야 합니다. 이 작업은 열의 수가 `SELECT` 문 또는 표 디자인의 일부로 다양한 열에 대해 더 작은 데이터 형식 선택. New Relic 계정이 있는 경우 [New Relic APM 오류 페이지](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) 및 [New Relic APM 데이터베이스 페이지](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time), 및 [New Relic 로그](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) 관련 쿼리를 검색합니다.
1. 빠른 수정을 위해 일시적으로 다음을 요청할 수 있습니다. `max_allowed_packet` 다음과 같은 경우 크기 증가 [티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)그러나 값이 너무 크면 네트워크 정체가 발생하여 복제 장애가 발생할 수 있으므로 고객 엔지니어링 팀의 판단에 따라 이 작업을 수행할 수 있습니다.
1. 가장 좋은 방법은 일부 대용량 데이터베이스 테이블에 대해 CLI에서 다음 명령을 실행하는 것입니다.

   ```
   show table status like [table name to match]
   ```

   이러한 테이블에서 실행 중인 쿼리를 평가하여 권장 사항을 초과하는지 여부를 확인합니다 `max_allowed_packet` 크기: 16MB 1단계에서 동일한 프로세스를 따라 이러한 쿼리에서 반환되는 데이터를 줄입니다.

## 관련 읽기

* [설치 안내서 > MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) 개발자 설명서에서 확인할 수 있습니다.
* [데이터베이스를 업로드하면 MySQL에 대한 연결이 끊어집니다.](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) 을 참조하십시오.
* [클라우드 인프라의 Adobe Commerce에 대한 데이터베이스 모범 사례](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) 을 참조하십시오.
* [데이터베이스 성능 문제 해결 모범 사례](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) 을 참조하십시오.
