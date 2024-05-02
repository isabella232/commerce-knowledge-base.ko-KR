---
title: 데이터 마이그레이션 도구 문제 해결
description: 이 문서에서는 데이터 마이그레이션 도구를 실행할 때 발생할 수 있는 오류에 대한 솔루션을 제공합니다.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# 데이터 마이그레이션 도구 문제 해결

이 문서에서는 데이터 마이그레이션 도구를 실행할 때 발생할 수 있는 오류에 대한 솔루션을 제공합니다.

## 소스 문서/필드가 매핑되지 않음 {#source-documents-fields-not-mapped}

### 오류 메시지

* ```bash    Source documents are not mapped: <EXTENSION_TABLE>    ```
* ```bash    Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <EXTENSION_FIELD>    ```

드문 경우지만 메시지에

```bash
Destination documents
```

또는

```bash
Destination fields
```

소스 조각 대신

### 원인

일부 Adobe Commerce 버전 1 엔티티(대부분의 경우 확장에서 가져옴)가 Adobe Commerce 버전 2 데이터베이스에 없습니다.

이 메시지는 데이터 마이그레이션 도구에서 내부 테스트를 실행하여 테이블 및 필드가 일관되는지 확인하기 때문에 나타납니다. *소스* (Adobe Commerce 1) 및 *대상* (Adobe Commerce 2) 데이터베이스.

### 가능한 해결 방법

* 에서 해당 Adobe Commerce 2 확장 설치 [Commerce Marketplace](https://marketplace.magento.com/).     충돌하는 데이터가 자체 데이터베이스 구조 요소를 추가하는 확장에서 비롯된 경우, 동일한 확장의 Adobe Commerce 2 버전에서 이러한 요소를 대상(Adobe Commerce 2) 데이터베이스에 추가하여 문제를 해결할 수 있습니다.
* 사용 `-a` 오류 자동 해결 및 마이그레이션 중지 방지 도구 실행 시 인수
* 문제가 있는 데이터를 무시하도록 도구를 구성합니다.

데이터베이스 엔티티를 무시하려면 `<ignore>` 태그로 엔티티의 `map.xml` 다음과 같은 파일:

```xml
...
    <source>
        <document_rules>
            ...
            <!-- Ignore `sales_flat_invoice_grid` table -->
            <ignore>
                <document>sales_flat_invoice_grid</document>
            </ignore>
            <!-- Ignore `address_id` field of `sales_flat_order_address` table -->
            <ignore>
                <field>sales_flat_order_address.address_id</field>
            </ignore>
            ...
        </document_rules>
    </source>
    ...
```

>[!WARNING]
>
>맵 파일로 엔티티를 무시하거나 `-a` 옵션에서 Adobe Commerce 2 스토어에 영향을 받는 데이터가 필요하지 않은지 확인하십시오.

## 클래스가 레코드에서 매핑되지 않았습니다. {#class-does-not-exist-but-mentioned}

### 오류 메시지

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### 원인

다음을 수행하는 동안 Adobe Commerce 1 코드베이스의 클래스를 Adobe Commerce 2 코드베이스에서 찾을 수 없습니다. [EAV 마이그레이션 단계](https://devdocs.magento.com/guides/v2.3/migration/migration-tool-internal-spec.html#eav) 개발자 설명서에서 확인할 수 있습니다. 대부분의 경우 누락된 클래스는 [확장](https://glossary.magento.com/extension).

### 가능한 해결 방법

* 해당 Adobe Commerce 2 확장을 설치합니다.
* 문제를 일으키는 속성을 무시합니다.    이에 대해 속성을 `ignore` 다음에서 그룹: `eav-attribute-groups.xml.dist` 파일.
* 를 사용하여 클래스 매핑 추가 `class-map.xml.dist` 파일.

## 외래 키 제약 조건 실패

### 오류 메시지 텍스트

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### 원인

에 데이터베이스 레코드가 없습니다. `parent_table` 대상 `field_id` / `child_table` 이(가) 을 가리킵니다.

### 가능한 해결 방법

다음에서 레코드 삭제 `child_table` , 필요하지 않은 경우.

레코드를 유지하려면 `Data Integrity Step` 데이터 마이그레이션 도구 수정 `config.xml` .

## URL 재작성에서 중복 항목

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### 원인

다음 `Target path` URL에서 재작성은 다음의 고유한 쌍으로 지정해야 합니다. `Request path` + `Store ID` . 이 오류는 동일한 항목을 사용하는 두 개의 항목을 보고합니다 `Request path` + `Store ID` 다른 두 항목과 연결 `Target path` 값.

### 가능한 해결 방법

활성화 `auto_resolve_urlrewrite_duplicates` 의 옵션 `config.xml` 파일.

이 구성은 의 충돌하는 레코드에 해시 문자열을 추가합니다. [URL](https://glossary.magento.com/url) 를 재작성하고 명령줄 인터페이스에 해결 결과를 표시합니다.

## 엔티티 불일치 {#mismatch-of-entities}

### 오류 메시지

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### 원인

이 오류는 볼륨 확인 단계에서 발생합니다. 즉, 문서의 Adobe Commerce 2 데이터베이스 레코드 수가 Adobe Commerce 1과 동일하지 않습니다.

고객이 마이그레이션하는 동안 주문하면 레코드가 누락됩니다.

### 가능한 해결 방법

에서 데이터 마이그레이션 도구 실행 `Delta` 증분 변경 사항을 전송하는 모드입니다.

## Deltalog가 설치되지 않았습니다. {#deltalog-is-not-installed}

### 오류 메시지

```bash
Deltalog for <TABLE_NAME> is not installed
```

### 원인

이 오류는 다음 중 발생합니다. [증분 마이그레이션](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-delta.html) (개발자 설명서에서) 데이터에 대한 변경 내용. 이것은 deltalog 표(접두사 포함)를 의미합니다 `m2_cl_*`)을(를) Adobe Commerce 1 데이터베이스에서 찾을 수 없습니다. 이 도구는 다음 기간 동안 이러한 테이블을 설치합니다. [데이터 마이그레이션](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-data.html) (개발자 설명서에 있음)뿐만 아니라 변경 사항을 추적하고 deltalog 테이블을 채우는 데이터베이스 트리거도 제공됩니다.

오류의 한 가지 이유는 *복사* 라이브 스토어 자체가 아니라 라이브 Adobe Commerce 1 스토어. 마이그레이션된 적이 없는 라이브 Adobe Commerce 1 스토어에서 복사본을 만들 때 복사본에 델타 마이그레이션을 완료하는 데 필요한 트리거와 추가 deltalog 테이블이 포함되어 있지 않으므로 마이그레이션이 실패합니다. 데이터 마이그레이션 툴은 AC1과 AC2의 DB를 비교하여 차이점을 마이그레이션하지 않습니다. 대신, 이 도구는 후속 델타 마이그레이션을 수행하기 위해 첫 번째 마이그레이션 중에 설치된 트리거 및 Deltalog 테이블을 사용합니다. 이러한 경우 라이브 Adobe Commerce 1 DB의 복사본에는 데이터 마이그레이션 도구가 마이그레이션을 수행하는 데 사용하는 트리거 및 카탈로그 테이블이 포함되지 않습니다.

### 가능한 해결 방법

마이그레이션 문제를 해결하기 위해 Adobe Commerce 1 데이터베이스의 복사본에서 마이그레이션 프로세스를 테스트하는 것이 좋습니다. 사본의 문제를 해결한 후 라이브 Adobe Commerce 1 데이터베이스에서 마이그레이션 프로세스를 다시 시작합니다. 이를 통해 원활한 마이그레이션 프로세스를 보장할 수 있습니다.
