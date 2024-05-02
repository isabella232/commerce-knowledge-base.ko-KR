---
title: CSV 가져오기 후 새 고객이 고객 그리드에 표시되지 않음
description: 이 문서에서는 ".csv" 파일에서 가져온 후 **Customers** &gt; **All customers** 아래에 새 고객이 표시되지 않을 때 발생하는 문제를 해결합니다. 해결 방법은 'customer_grid' 인덱서를 "저장 시 업데이트" 모드로 설정하고 고객 그리드를 수동으로 다시 인덱싱하는 것입니다.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# CSV 가져오기 후 새 고객이 고객 그리드에 표시되지 않음

이 문서에서는 새 고객이에 표시되지 않는 문제에 대한 해결 방법을 제공합니다 **고객** > **모든 고객** 에서 가져오기 후 `.csv` 파일. 해결 방법은 를 설정하는 것입니다. `customer_grid` 인덱서를 &quot;저장 시 업데이트&quot; 모드로 변경하고 고객 그리드를 수동으로 다시 인덱싱합니다.

## 영향을 받는 버전

* Adobe Commerce 온-프레미스 2.2.0 이상
* cloud infrastructure 2.2.0 이상 버전의 Adobe Commerce

## 문제

에서 새 고객을 가져온 후 `.csv` 기본 Adobe Commerce 가져오기 기능을 사용하는 파일은에서 새 고객 레코드를 보지 못할 수 있습니다. **고객** > **모든 고객** 를 수동으로 다시 색인화할 때까지 관리자 `customer_grid` 인덱서.

## 원인

Adobe Commerce 2.2.0 이상의 &quot;일정에 따라 업데이트&quot; 인덱싱 모드는 `customer_grid` 성능 문제로 인한 인덱서입니다.

## 솔루션

구성 `customer_grid` 저장 시 업데이트 모드를 사용하여 다시 인덱싱할 인덱서입니다. 이렇게 하려면 다음 단계를 수행합니다.

1. Commerce 관리자에 로그인합니다.
1. 클릭 **시스템** > **도구** > **색인 관리**.
1. Customer Grid Indexer 옆에 있는 확인란을 선택합니다.
1. 다음에서 **작업** 드롭다운 목록에서 다음을 선택합니다. *저장 시 업데이트*.
1. 클릭 **제출**.

또한 수동으로 리인덱싱하는 것이 좋습니다. `customer_grid` 색인이 최신 상태이고 cron에서 작업할 수 있도록 색인화 모드를 구성한 후 색인화합니다. 수동으로 다시 색인화하려면 다음 명령을 사용합니다.

`bin/magento indexer:reindex customer_grid`

## 추가 정보

개발자 설명서 관련 항목 링크:

* [색인화 개요](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [인덱서 관리](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
