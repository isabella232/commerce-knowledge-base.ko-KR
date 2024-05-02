---
title: MariaDB 10.6의 Adobe Commerce Cloud 2.4.6에서 복제본 문제 읽기
description: 이 문서에서는 MariaDB 10.6을 사용하여 Adobe Commerce Cloud 2.4.6에서 읽기 전용 복제본 문제를 해결하는 방법에 대해 설명합니다.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# MariaDB 10.6의 Adobe Commerce Cloud 2.4.6에서 복제본 문제 읽기

이 문서에서는 MariaDB 10.6+와 함께 Adobe Commerce Cloud 2.4.6에서 읽기 전용 복제본을 사용할 때 예기치 않은 비헤이비어에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* MariaDB 10.6+
* 클라우드 인프라의 Adobe Commerce 2.4.6

## 문제

중요하지 않은 읽기에 잘못된 정보가 표시됩니다.

## 원인

다음 `slave_parallel_mode` 데이터베이스의 구성이 기본적으로 (으)로 변경되었습니다. *최적화* 값은 다음과 같아야 합니다. *보수주의자*&#x200B;및 `synchronous_replication` ece-Tools 의 값은 기본적으로 *true* 값은 다음과 같아야 합니다. *false*.

## 솔루션

1. 다음을 확인하십시오. `slave_parallel_mode` 매개 변수가 로 설정되어 있습니다. *보수주의자* (다음을 수행해야 합니다. [지원 티켓 올리기](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) 값이 로 표시되지 않는 경우 *보수주의자*). 확인하려면 다음 명령을 실행합니다.

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. 업데이트 `.magento.env.yaml` 데이터베이스 구성 대상:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



데이터베이스 구성을 업데이트하는 단계는 다음을 참조하십시오. [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) Commerce on Cloud Infrastructure 안내서의 변수 배포 항목.


## 관련 읽기

* [배포를 위한 환경 변수 구성](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) Commerce on Cloud Infrastructure Guide를 참조하십시오.
* [데이터베이스 구성 모범 사례](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) 를 참조하십시오.
