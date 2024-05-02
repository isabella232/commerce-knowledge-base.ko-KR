---
title: 404 카탈로그 가격 규칙 일정 업데이트가 수행되면 스토어 프런트에 오류 발생
description: 이 문서에서는 카탈로그 가격 규칙 업데이트를 만든 후 시작 시간을 나중에 편집한 후 모든 스토어 전면 페이지에서 404 오류를 가져오는 것과 관련된 알려진 Adobe Commerce 2.2.1 문제를 해결하는 데 필요한 단계 및 패치를 제공합니다. 이 문제를 해결하려면 패치를 적용해야 합니다.
exl-id: 7ea148a5-56cb-479a-8b2f-fae8b3bd4b22
feature: Cache, Catalog Management, Marketing Tools, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# 404 카탈로그 가격 규칙 일정 업데이트가 수행되면 스토어 프런트에 오류 발생

이 문서에서는 카탈로그 가격 규칙 업데이트를 만든 후 시작 시간을 나중에 편집한 후 모든 스토어 전면 페이지에서 404 오류를 가져오는 것과 관련된 알려진 Adobe Commerce 2.2.1 문제를 해결하는 데 필요한 단계 및 패치를 제공합니다. 이 문제를 해결하려면 패치를 적용해야 합니다.

## 문제

Storefront 페이지를 사용할 수 없게 되어 404 오류가 반환됩니다. 이 문제는 활성 카탈로그 가격 규칙 업데이트 기한이 지난 후에 나타나며, 이 업데이트의 시작 날짜가 초기 생성 후에 편집되었습니다.

<u>재현 단계</u>:

1. Commerce 관리에서 아래에 새 카탈로그 가격 규칙을 만듭니다. **마케팅** > **프로모션** > **카탈로그 가격 규칙**.
1. 다음에서 **카탈로그 가격 규칙** 그리드, 클릭 **편집,** 새 업데이트 예약 및 설정 **상태** 끝 *활성.*
1. 다음으로 이동 **콘텐츠** > **컨텐츠 스테이징** > **대시보드.**
1. 최근에 만든 업데이트를 선택하고 시작 시간을 변경합니다.
1. 변경 사항을 저장합니다.

<u>예상 결과</u> :

업데이트 시작 일자가 발효되면 카탈로그 가격 규칙이 성공적으로 적용됩니다.

<u>실제 결과</u> :

업데이트 시작 날짜가 발효되면 404 오류를 반환하는 상점 내 모든 카탈로그 및 제품을 사용할 수 없게 됩니다.

## 솔루션

카탈로그 페이지를 복원하고 카탈로그 가격 규칙 업데이트 기능을 완전히 사용하려면 패치를 설치하고 수동으로 및 관리자에서 규칙을 삭제하고 데이터베이스의 잘못된 링크를 수정해야 합니다. 카탈로그 가격 규칙도 다시 만들어야 합니다.

다음은 필수 단계에 대한 자세한 설명입니다.

1. [패치 적용](#patch).
1. Commerce 관리에서 문제(시작 시간이 업데이트된 경우)와 관련된 카탈로그 가격 규칙을 삭제합니다. 이렇게 하려면 아래의 규칙 페이지를 엽니다. **마케팅** > **프로모션** > **카탈로그 가격 규칙**, 및 클릭 **규칙 삭제**.
1. 데이터베이스에 액세스하면에서 관련 레코드를 수동으로 삭제합니다. `catalogrule` 테이블.
1. 데이터베이스에서 잘못된 링크를 수정합니다. 다음을 참조하십시오. [관련 단락](#fix_links) 을 참조하십시오.
1. Commerce 관리자 아래의 **마케팅**&#x200B;로 이동합니다. **프로모션** > **카탈로그 가격 규칙**&#x200B;필요한 구성을 사용하여 새 규칙을 만듭니다.
1. 아래의 브라우저 캐시 지우기 **시스템** > **캐시 관리**.
1. cron 작업이 올바르게 구성되어 있고 성공적으로 실행되었는지 확인하십시오.

## 패치 {#patch}

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-7392\_EE\_2.2.1\_COMPOSER\_v2.patch 다운로드](assets/MDVA-7392_EE_2.2.1_COMPOSER_v2.patch.zip)

## 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* Adobe Commerce 2.2.1

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 클라우드 인프라 2.2.0의 Adobe Commerce - 2.2.4
* Adobe Commerce 온-프레미스 2.2.0 및 2.2.2 - 2.2.4

## 패치 적용 방법

자세한 내용은 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 을 참조하십시오.

## DB의 스테이징에 대한 잘못된 링크 수정 {#fix_links}

>[!WARNING]
>
>데이터베이스를 조작하기 전에 데이터베이스 백업을 만드는 것이 좋습니다. 또한 개발 환경에서 쿼리를 먼저 테스트하는 것이 좋습니다.

에 대한 링크가 잘못된 행을 수정하려면 다음 단계를 따르십시오. `staging_update` 테이블.

1. 에 대한 링크가 잘못되었는지 확인 `staging_update` 테이블이 다음 위치에 있음: `flag` 테이블. 이것들은 다음과 같은 위치에 있는 레코드입니다. `flag_code=staging`.
1. 에서 잘못된 버전 식별 `flag` 다음 쿼리를 사용하는 테이블:

   ```sql
   SELECT flag_data FROM flag WHERE flag_code = 'staging';
   ```

1. 다음에서 `staging_update` 테이블에서 현재(부적합한) 버전보다 작은 기존 버전을 선택하고 두 숫자인 버전 값을 다시 가져옵니다. 이전 버전이 의 최대 버전일 때의 상황을 방지하기 위해 이전 버전이 아니라 이 버전을 사용합니다. `staging_update` 적용할 수 있는 테이블이며 우리는 여전히 다시 적용해야 합니다.

   ```sql
   SELECT id FROM staging_update WHERE id < %current_id% ORDER BY id DESC LIMIT 1, 1
   ```

   응답으로 받은 버전이 올바른 버전입니다. `id`.

1. 에 잘못된 링크가 있는 행의 경우 `flag` 테이블, 설정 `flag_data` 유효한 버전 id가 포함될 데이터에 대한 값입니다. 이렇게 하면 색인 재지정 단계에서 성능을 절약할 수 있으며 모든 엔티티를 색인화하지 않아도 됩니다.

   ```sql
   UPDATE flag SET flag_data=REPLACE(flag_data, '%invalid_id%', '%new_valid_id%') WHERE flag_code='staging';
   ```

<u>예:</u>

```sql
SELECT flag_data FROM flag WHERE flag_code = 'staging'; <code class="language-bash">Response < 2.2 version</code>
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| a:1:{s:15:"current_version";s:10:"1490005140";} |
```

```bash
+-------------------------------------------------+
```

```bash
Response from 2.2 version
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| {"current_version":"1490005140"} |
```

```bash
+-------------------------------------------------+
```

```sql
SELECT id FROM staging_update WHERE id < 1490005140 <code class="language-sql">ORDER BY id DESC LIMIT 1, 1</code>;
```

```bash
Response:
```

```bash
1490005138
```

```sql
UPDATE flag SET flag_data=REPLACE(flag_data, '1490005140', '1490005138') WHERE flag_code='staging';
```

## 첨부 파일
