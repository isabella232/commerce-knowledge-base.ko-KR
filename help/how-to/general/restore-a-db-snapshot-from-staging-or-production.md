---
title: 스테이징 또는 프로덕션에서 DB 스냅샷 복원
description: 이 문서에서는 클라우드 인프라의 Adobe Commerce에서 스테이징 또는 프로덕션에서 DB 스냅샷을 복원하는 방법을 보여 줍니다.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: b9e72ff8d541ad01788e5198e03abcb46a1bd11f
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# 에서 DB 스냅샷 복원 [!DNL Staging] 또는 [!DNL Production]

이 문서에서는 DB를 복원하는 방법을 보여 줍니다 [!DNL snapshot] 출처: [!DNL Staging] 또는 [!DNL Production] Adobe Commerce on Cloud Pro 인프라

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

사용 사례에 가장 적합한 항목 선택:

* [방법 1: 데이터베이스 전송 [!DNL dump] 로컬 시스템으로 가져와서 가져오기](#meth2).
* [방법 2: 데이터베이스 가져오기 [!DNL dump] 서버에서 직접](#meth3).

## 방법 1: 데이터베이스 전송 [!DNL dump] 로컬 시스템으로 가져와서 가져오기 {#meth2}

단계는 다음과 같습니다.

1. 사용 [!DNL sFTP]를 클릭하고 데이터베이스가 있는 위치로 이동합니다. [!DNL snapshot] 이(가) 배치되었습니다(일반적으로 의 첫 번째 서버/노드). [!DNL cluster] (예: `/mnt/recovery-<recovery_id>`). 참고: 프로젝트가 Azure 기반 프로젝트인 경우, 즉 프로젝트 URL은 https://us-a1.magento.cloud/projects/ 과 비슷합니다.&lt;cluster_id>스냅샷이에 배치됩니다. `/mnt/shared/<cluster ID>/all-databases.sql.gz` 또는 `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` 대신,

   참고: Azure 프로젝트의 스냅숏 형식은 다르며 가져올 수 없는 다른 데이터베이스를 포함합니다. 스냅샷을 가져오기 전에 추가 단계를 수행하여 적절한 데이터베이스를 추출한 후 덤프를 가져와야 합니다.

   프로덕션의 경우:

   ```sql
   cd /mnt/shared/<cluster ID/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID>.sql 
   sed -n '/^-- Current Database: `<cluster ID>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID>.sql gzip <cluster ID>.sql
   zcat <cluster ID>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

   스테이징의 경우:

   ```sql
   cd /mnt/shared/<cluster ID/ | cd /mnt/shared/<cluster ID_stg>
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `wyf2o4zlrljjs`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. 데이터베이스 복사 [!DNL dump file] (예: `<cluster ID>.sql.gz` 대상 [!DNL Production] 또는 `<cluster ID_stg>.sql.gz` 대상 [!DNL Staging])을 클릭하여 로컬 컴퓨터에 연결하십시오.
1. 다음을 설정했는지 확인하십시오. [!DNL SSH tunnel] 데이터베이스에 원격으로 접속하려면 [[!DNL SSH] 및 [!DNL sFTP]: [!DNL SSH tunneling]](https://devdocs.magento.com/cloud/env/environments-ssh.html#env-start-tunn) 개발자 설명서에서 확인할 수 있습니다.
1. 데이터베이스에 연결합니다.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] 데이터베이스; [!DNL MariaDB] 프롬프트에서 다음을 입력합니다.

   (대상 [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (대상 [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. 다음 명령을 입력하여 [!DNL snapshot]:

   (대상 [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (대상 [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## 방법 2: 데이터베이스 가져오기 [!DNL dump] 서버에서 직접 {#meth3}

단계는 다음과 같습니다.

1. 데이터베이스가 있는 위치로 이동합니다. [!DNL snapshot] 이(가) 배치되었습니다(일반적으로 의 첫 번째 서버/노드). [!DNL cluster] (예: `/mnt/recovery-<recovery_id>`).
1. 종료 [!DNL drop] 클라우드 데이터베이스를 다시 생성하고 먼저 데이터베이스에 연결합니다.

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] 데이터베이스; [!DNL MariaDB] 프롬프트에서 다음을 입력합니다.

   (대상 [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (대상 [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. 다음 명령을 입력하여 [!DNL snapshot]:

   (대상 [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (대상 [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## 관련 읽기

개발자 설명서에서:

* [코드 가져오기: 데이터베이스를 가져옵니다.](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html#cloud-import-db)
* [[!DNL Snapshots] 및 [!DNL backup] 관리: [!DNL Dump] 데이터베이스](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump)
