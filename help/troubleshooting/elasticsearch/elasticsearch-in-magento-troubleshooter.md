---
title: Adobe Commerce 문제 해결사의 Elasticsearch
description: Adobe Commerce의 Elasticsearch 문제는 Elasticsearch 문제 해결사 도구를 사용하여 해결할 수 있습니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다.
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Adobe Commerce 문제 해결사의 Elasticsearch

Adobe Commerce의 Elasticsearch 문제는 Elasticsearch 문제 해결사 도구를 사용하여 해결할 수 있습니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다.

>[!WARNING]
>
>Adobe Commerce on cloud infrastructure의 경우 48시간 동안 인프라 팀에 통지하지 않으면 서비스 업그레이드를 프로덕션 환경으로 푸시할 수 없습니다. 이는 인프라 지원 엔지니어가 운영 환경에 대한 가동 중지 시간을 최소화하면서 원하는 기간 내에 구성을 업데이트할 수 있도록 해야 하기 때문에 필요합니다. 따라서 변경 사항이 프로덕션에 적용되기 48시간 전 [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 필요한 서비스 업그레이드에 대한 세부 정보를 제공하고 업그레이드 프로세스를 시작할 시간을 명시합니다.

## 1단계 - Elasticsearch 문제 확인 {#step-1}

+++**Elasticsearch과 관련된 문제입니까?**

오류 메시지, &quot;에 의해 표시된 Elasticsearch 문제&#x200B;_클러스터에서 활성 노드를 찾을 수 없음&quot;,_ 누락된 제품 및 이전 제품 정보의 표시.

a. 예 - 진행합니다. [2단계](#step-2).\
b. 아니오 - 다음에서 관련 검색어를 다시 검색합니다. [Adobe Commerce 도움말 센터 기술 자료](https://support.magento.com/hc).

+++

## 2단계 - 설치 문제 확인 {#step-2}

+++**새로운 Elasticsearch 설치입니까?**

a. 예 - [Elasticsearch이 제대로 설치되었는지 확인합니다.](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) 또한 클라우드 인프라 2.3.1 이상에서 Adobe Commerce에 있는지 확인합니다. 클라우드 인프라(버전 2.3.1 이상)에서 Adobe Commerce으로 업그레이드하고 6.x 이전 버전의 Elasticsearch에 있는 판매자는 배포 시 오류가 발생할 수 있습니다. 이 문제를 해결하려면 Elasticsearch 클라이언트 모듈과 Elasticsearch 서비스가 권장 최신 버전이어야 합니다. 단계는 를 참조하십시오. [cloud infrastructure 2.3.1 이상에서 Adobe Commerce 업그레이드 후 Elasticsearch 문제](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md).\
b. 아니요 - 클러스터의 상태를 확인합니다. Pro 스테이징 또는 프로덕션 환경을 사용하는 경우 이 명령을 실행합니다. `curl -m1 localhost:9200/_cluster/health?pretty`. 통합 환경(모든 스타터 분기 포함)에 있는 경우 를 실행합니다 `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`. 다음으로 진행 [3단계](#step-3).

+++

## 3단계 - Elasticsearch 클러스터를 사용할 수 있는지 확인 {#step-3}

+++**서비스 응답 받았습니까?**

a. 예 - 진행합니다. [4단계](#step-4).\
b. 아니요 - 진행합니다. [9단계](#step-9).

+++

## 4단계 - Elasticsearch 클러스터 정상 확인 {#step-4}

+++**녹색 응답?**

a. 예 - Elasticsearch을 데이터 처리에 사용할 수 있으며 리인덱싱이 작동해야 합니다. 다음으로 진행 [5단계](#step-5).\
b. 아니요 - 노란색 또는 빨간색은 노드 간 연결에 문제가 있음을 의미하며 일부 데이터를 사용할 수 없을 수도 있습니다. 노란색이면 명령을 실행합니다. `php bin/magento config:show catalog/search/engine` 검색 엔진을 확인합니다. 다음으로 진행 [6단계](#step-6). 빨간색이면, [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 5단계 - 검색 작동 확인 {#step-5}

+++**검색 문제?**

증상에는 제품 없음, 빈 범주 또는 제품 또는 제품 범주가 올바르지 않은 업데이트가 없을 수 있습니다.

a. 예 - 이 명령을 실행하여 카탈로그 검색 상태를 확인합니다. `php bin/magento indexer:status`. 다음으로 진행 [8단계](#step-8).\
b. 아니요 - 명령 실행: `php bin/magento config:show catalog/search/engine`. 다음으로 진행 [6단계](#step-6).

+++

## 6단계 - ElasticSuite 확인 {#step-6}

+++**ElasticSuite를 사용 중입니까?**

a. 예 - 다음 명령을 실행하여 ElasticSuite가 현재 버전인지 확인합니다. `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'` 이 버전이 더 이상 사용되지 않거나 권장되는지 확인하려면 [Github: Smile-SA/탄력적인 제품군](https://github.com/Smile-SA/elasticsuite). ElasticSuite가 최신 버전인 경우 다음으로 진행하십시오. [10단계](#step-10).\
b. 아니요 - 다음으로 진행 [7단계](#step-7).

+++

## 7단계 - ECE-tools 최신 확인 {#step-7}

+++**ECE-tools 가 최신 버전입니까?**

다음 명령을 실행합니다. `php ./vendor/bin/ece-tools -V` ECE-tools 버전을 확인하십시오. 다음 항목입니까? [최신 버전의 ECE-tools](https://github.com/magento/ece-tools/releases)?

a. 예 - 진행합니다. [5a단계](#step-5).\
b. 아니요 - ECE-tools 를 최신 버전으로 업그레이드합니다. 명령 실행 `php bin/magento config: show catalog/search/engine` 검색 엔진을 확인합니다. 다음으로 진행 [6단계](#step-6).

+++

## 8단계 - 리인덱싱 확인 {#step-8}

+++**다음에 있는 카탈로그 검색 상태 _처리 중_?**

a. 예 - 처리가 완료될 때까지 기다린 후 제품 범주가 업데이트되었는지 확인해야 합니다. 만약 없다면, [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. 아니요 - 카탈로그 검색 상태가 다음과 같은 경우 _색인 재지정 필요_ cli/터미널에서 실행: `php bin/magento cron:run`. 작동하지 않는 경우 다음을 실행합니다. `php bin/magento indexer:reindex`. 이렇게 해도 문제가 해결되지 않으면 [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 9단계 - yaml 구성 확인 {#step-9}

+++**`.yaml`파일이 최근 업데이트되었습니까?**

a. 예 - 확인 `.yaml` DevDocs를 참조하여 구성 Elasticsearch [Elasticsearch 설정: Elasticsearch을 활성화하려면](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml).\
b. 아니요 - [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 10단계 - 추적 인덱스 확인 {#step-10}

+++**추적 인덱스가 나열됩니까?**

실행 `curl elasticsearch.internal:9200/_cat/indices` (모든 스타터 분기가 포함된 통합 환경에 있는 경우). Pro 스테이징 또는 프로덕션 환경 실행 중인 경우 `curl localhost:9200/_cat/indices`. 추적 인덱스가 나열됩니까? 다음에 대한 출력을 확인합니다.`_tracking_log_`.

a. 예 - ElasticSuite 2.8.0 이전 버전을 사용하고 있는 경우 [ElasticSuite 2.8.0으로 업그레이드하여 추적 인덱스 보존을 조정하거나 추적을 비활성화합니다](https://support.magento.com/hc/en-us/articles/360035266131?). 즉시 업그레이드할 수 없는 경우 다음을 수행할 수 있습니다. [cron을 만들어 추적 인덱스 제거](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md). 그러나 이로 인해 성능 문제가 발생할 수 있습니다. ElasticSuite 2.8.0으로 업그레이드하거나 추적 인덱스를 제거하면 명령을 실행합니다(Pro 스테이징 또는 프로덕션 환경에 있는 경우).`localhost:9200/_cat/allocation?v` 사용 가능한 공간을 확인합니다. 통합 환경(모든 스타터 분기 포함) 중 하나에 있는 경우 를 실행합니다 `elasticsearch.internal:9200/_cat/allocation?v`. 다음으로 진행 [11단계](#step-11).\
b. 아니요 - Pro 스테이징 중이거나 프로덕션 환경을 실행하는 경우 `localhost:9200/_cat/allocation?v` 사용 가능한 공간을 확인합니다. 통합 환경(모든 스타터 분기 포함) 중 하나에 있는 경우 를 실행합니다 `elasticsearch.internal:9200/_cat/allocation?v`. 다음으로 진행 [11단계](#step-11).

+++

## 11단계 - 특정 오류 조회 {#step-11}

+++**특정 오류?**

Adobe Commerce 및 ES 로그, 확장 및 사용자 지정 코드.

a. 예 - Adobe Commerce 도움말 센터 문제 해결 문서 검토 [Elasticsearch이 제대로 설치되었는지 확인](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) 또는 [ElasticSuite 플러그인을 사용할 때 Elasticsearch이 충돌하거나 메모리 부족 문제가 발생합니다](https://support.magento.com/hc/en-us/articles/360035266131).\
b. 아니요 - 진행합니다. [12단계](#step-12).

+++

## 12단계 - 사용 가능한 스토리지 확인 {#step-12}

+++**스토리지 사용량 85% 이상**

a. 예 - 사용 가능한 스토리지를 늘려야 합니다. DevDocs 참조[Elasticsearch 설정: Elasticsearch을 활성화하려면](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml). 그런 다음 를 실행합니다. `localhost:9200/_cat/allocation?v` (Pro 스테이징 또는 프로덕션 환경에 있는 경우). 모든 스타터 분기를 포함하는 통합 환경 중 하나에 있는 경우 다음을 실행합니다. `elasticsearch.internal:9200/_cat/allocation?v`. 다음으로 진행 [11단계](#step-11).\
b. 아니요 - [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[1단계로 돌아가기](#step-1)
