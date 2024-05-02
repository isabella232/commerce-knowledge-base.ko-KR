---
title: 클라우드 인프라의 Adobe Commerce에서 데이터베이스 덤프 만들기
description: 이 문서에서는 Adobe Commerce on cloud infrastructure에서 데이터베이스(DB) 덤프를 생성하는 가능한(및 권장되는) 방법에 대해 설명합니다.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 0948b2a94ee4f2a355e7c024a09929f0ad223783
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce에서 데이터베이스 덤프 만들기

이 문서에서는 Adobe Commerce on cloud infrastructure에서 데이터베이스(DB) 덤프를 생성하는 가능한(및 권장되는) 방법에 대해 설명합니다.

하나의 변형(옵션)만 사용하여 DB를 덤프하면 됩니다. 이러한 옵션은 모든 환경 유형(통합, 스테이징, 프로덕션) 및 모든 계획(Adobe Commerce on cloud infrastructure Starter 계획 아키텍처 및 Adobe Commerce on cloud infrastructure Pro 계획 아키텍처)에 적용됩니다.

## 전제 조건: SSH를 환경에

이 문서에서 설명한 변형이 포함된 Adobe Commerce on cloud infrastructure의 DB를 덤프하려면 먼저 다음을 수행해야 합니다 [환경에 SSH 추가](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>옵션 1을 선택하든 옵션 2를 선택하든 데이터베이스 보조 노드에 대해 사용량이 적은 시간 동안 명령을 실행하십시오.

## 옵션 1: db-dump (**ece-tools, 권장**)

다음을 사용하여 DB를 덤프할 수 있습니다. [ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) 명령:

```php
vendor/bin/ece-tools db-dump
```

권장되는 가장 안전한 옵션입니다.

다음을 참조하십시오 [데이터베이스 덤프(ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) Commerce on Cloud Infrastructure Guide를 참조하십시오.

## 옵션 2: mysqldump

>[!WARNING]
>
>데이터베이스 클러스터에 대해 이 명령을 실행하지 마십시오. 클러스터는 기본 데이터베이스에 대해 실행되는지 보조 데이터베이스에 대해 실행되는지 여부를 구분하지 않습니다. 클러스터가 기본 데이터베이스에 대해 이 명령을 실행하는 경우 덤프가 완료될 때까지 데이터베이스가 쓰기를 실행할 수 없으며 성능 및 사이트 안정성에 영향을 미칠 수 있습니다.

기본 MySQL을 사용하여 DB를 덤프할 수 있습니다. `mysqldump` 명령입니다.

전체 명령은 다음과 같습니다.

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

다음을 실행하여 생성된 데이터베이스 백업 `mysqldump` 명령 및 저장 위치 `\tmp`를 이 위치에서 이동해야 합니다. 에서 저장 공간을 차지해서는 안 됩니다. `\tmp` (문제가 발생할 수 있음).

DB 자격 증명(호스트, 사용자 이름 및 암호)을 얻으려면 `MAGENTO_CLOUD_RELATIONSHIPS` 환경 변수:

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**관련 설명서:**

* [mysqldump - 데이터베이스 백업 프로그램](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) 공식 MySQL 설명서에서 참조할 수 있습니다.
* [클라우드별 변수](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (참조 `MAGENTO_CLOUD_RELATIONSHIPS`Commerce )을 참조하십시오.
