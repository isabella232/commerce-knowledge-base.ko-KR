---
title: Adobe Commerce 데이터베이스 숫자 값이 범위를 벗어남, 'INT' ~ 'BIGINT'
description: 이 문서에서는 가격 변경, 제품 삭제 및 복제와 같은 제품 업데이트를 저장할 수 없는 경우에 대한 솔루션을 제공합니다.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Adobe Commerce 데이터베이스 숫자 값이 범위를 벗어났습니다. `INT` 끝 `BIGINT`

>[!WARNING]
>
>이 문서의 솔루션을 구현하기 전에(`INT` 끝 `BIGINT` 스키마 업데이트) 판매자는 항상 변경할 필드에 다른 테이블에 대한 외래 키 관계가 없는지 확인해야 합니다. 필드에 다른 테이블에 대한 외래 키 관계가 있는 경우 관련 필드가 여전히 존재하기 때문에 문제가 발생합니다 `INT`. 다음 쿼리를 사용하여 이를 확인할 수 있습니다. 이 쿼리는 주어진 테이블 필드에 대해 데이터베이스에서 사용할 수 있는 외래 키 관계를 나열합니다.
>
```mysql
>SELECT 
>     TABLE_NAME,COLUMN_NAME,CONSTRAINT_NAME,REFERENCED_TABLE_NAME,REFERENCED_COLUMN_NAME
>FROM
>   INFORMATION_SCHEMA.KEY_COLUMN_USAGE
>WHERE
>     REFERENCED_TABLE_SCHEMA = '<database_name>' AND
>     REFERENCED_TABLE_NAME = '<table_name>' AND
>     REFERENCED_COLUMN_NAME = '<table_field>';
>```

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 메서드) 모두 [지원되는 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

이 문서에서는 가격 변경, 제품 삭제 및 복제와 같은 제품 업데이트를 저장할 수 없는 경우에 대한 솔루션을 제공합니다.
오류 메시지가 표시될 수 있습니다 *재고 항목을 저장할 수 없습니다. 다시 시도하십시오.* 제품 업데이트 후 배포하지 못할 수 있습니다. 를 실행할 때 다음과 같은 MySQL 오류 메시지가 표시될 수도 있습니다 `php bin/magento setup:upgrade` (클라우드 인프라의 Adobe Commerce에서 이 오류는 배포 로그에 표시됩니다.)

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

이 문서에 설명된 솔루션은 다음과 같습니다.
* 업데이트 `[ AUTO_INCREMENT ]` 테이블에서 다음 값 또는
* `INT` 끝 `BIGINT` 스키마 업데이트

어떤 솔루션을 사용하는지는 문제의 원인이 무엇인지에 따라 다릅니다. 원인을 파악하려면 아래 단계를 참조하십시오.

## 원인 확인 단계


터미널에서 다음 명령을 실행하여 기본 키의 가장 높은 값을 확인합니다. `SELECT MAX(value_id) FROM catalog_product_entity_int;`

다음과 같은 경우 `max(value_id)` 보다 낮음 `max int(11) [ 4294967296 ]`및 `[ AUTO_INCREMENT ]` 이(가) 보다 크거나 같은 값을 갖습니다. `max int(11) [ 4294967296 ]`, 다음 고려 [업데이트 중 `[ AUTO_INCREMENT ]` 테이블에서 다음 값으로](#update-the-auto-increment-to-the-next-value-from-the-table). 그렇지 않으면 다음을 고려하십시오. [`INT` 끝 `BIGINT` 스키마 업데이트](#int_to_bigint_schema_update).

## 업데이트 `AUTO_INCREMENT` 테이블에서 다음 값으로 {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>테이블을 변경하기 전에 데이터베이스 백업을 수행합니다. 또한 사이트를 [유지 관리 모드](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). 또한 변경한 후 데이터베이스 테이블(변경된 테이블만)에서 MYSQL 최적화 명령을 실행하는 것이 좋습니다.

>[!NOTE]
>
>특정 테이블에서 최적화 명령을 실행하는 동안 사이트는 유지 관리 모드에 있어야 합니다. 이렇게 하면 테이블이 완전히 다시 빌드되고 테이블에서 데이터를 삭제한 후 공간이 확보됩니다.

표시된 값이 보다 작은 경우 `max int(11) [ 4294967296 ]` 아래 예제 터미널 출력에 표시된 것처럼 `[ AUTO_INCREMENT ]` 이(가) 보다 크거나 같은 숫자로 변경되었습니다. `max [ int(11) ]` 값.

```mariadb
MariaDB [xxx]> SELECT MAX(value_id) FROM catalog_product_entity_int;
+---------------------+
| MAX(source_item_id) |
+---------------------+
|          4283174130 |
+---------------------+
```

이 오류가 발생했는지 확인하려면 터미널에서 다음 명령을 실행합니다.

```
MariaDB [xxx]> show create table catalog_product_entity_int;

...
) ENGINE=InnoDB AUTO_INCREMENT=4294967297 DEFAULT CHARSET=utf8 COMMENT='Catalog Product Integer Attribute Backend Table';
```

위의 예에서 볼 수 있듯이 테이블을 출력합니다 `[ AUTO_INCREMENT ]` 이(가) 을(를) 보다 큰 수로 변경했습니다. `max int(11) [ 4294967296 ]`. 해결 방법은 를 업데이트하는 것입니다 `[ AUTO_INCREMENT]` 테이블에서 다음 값으로:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT` 끝 `BIGINT` 스키마 업데이트 {#int_to_bigint_schema_update}

그러나 다음 쿼리를 실행할 때는 `SELECT MAX(value_id) FROM catalog_product_entity_int;` 표시된 값이 보다 큽니다. `max int(11) [ 4294967296 ]`  다음 작업을 수행하는 것이 좋습니다. `INT` 끝 `BIGINT` 스키마 업데이트. 데이터 유형 `BIGINT` 에는 더 큰 값 범위가 있습니다.

방법은 다음과 같습니다.

1. 내부에 사용자 정의 모듈 만들기 *app/code/* 디렉토리.
1. 사용자 지정 모듈에서 *db_schema.xml*. 위치 *db_schema.xml* 데이터 유형을 다음으로 설정합니다. `BIGINT`.
1. 다음 콘텐츠를 추가한 다음 실행합니다 `bin/magento setup:upgrade` 위의 변경 사항을 해당 테이블에 적용합니다.

```
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
    <table name="catalog_product_entity_int">
        <column xsi:type="bigint" name="value_id" unsigned="false" nullable="false" identity="true"
                comment="Value ID"/>
    </table>
</schema>
```


## 관련 읽기

* [일반 MySQL 지침](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) Commerce 설치 안내서에서 확인할 수 있습니다.
* [데이터베이스를 업로드하면 MySQL에 대한 연결이 끊어집니다.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html) 을 참조하십시오.
* [클라우드 인프라의 Adobe Commerce에 대한 데이터베이스 모범 사례](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) 을 참조하십시오.
* [클라우드 인프라의 Adobe Commerce에서 가장 일반적인 데이터베이스 문제](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) 을 참조하십시오.
