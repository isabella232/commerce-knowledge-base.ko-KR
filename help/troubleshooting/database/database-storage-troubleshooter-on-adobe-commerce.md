---
title: Adobe Commerce의 데이터베이스 스토리지 문제 해결사
description: 이 문서는 데이터베이스에 문제가 있는 Adobe Commerce 고객을 위한 문제 해결사 도구입니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다. 증상 및 구성에 따라 문제 해결사가 데이터베이스의 공간 및 구성 문제를 해결하는 방법에 대해 설명합니다.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Adobe Commerce의 데이터베이스 스토리지 문제 해결사

이 문서는 데이터베이스에 문제가 있는 Adobe Commerce 고객을 위한 문제 해결사 도구입니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다. 증상 및 구성에 따라 문제 해결사가 데이터베이스의 공간 및 구성 문제를 해결하는 방법에 대해 설명합니다.

## 1단계 - 공간 문제가 있는 디렉터리 식별 {#step-1}

+++**가지고 계세요 `/tmp` 공간 부족으로 인한 문제입니까?**

이는 다음을 포함한 다양한 증상으로 나타낼 수 있습니다. `/tmp` 마운트가 꽉 찼거나, 사이트가 다운되었거나, 노드에 SSH를 사용할 수 없습니다. 다음과 같은 오류가 발생할 수도 있습니다. _장치에 남은 공간 없음(28)_. 다음 원인으로 인한 오류 목록의 경우: `/tmp` 가득 참, 검토 [/tmp 마운트 가득 참](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

아니면, `/data/mysql` 공간 부족으로 인한 문제입니까? 이는 사이트 중단, 고객이 장바구니에 제품을 추가할 수 없는 경우, 데이터베이스 연결 실패 및 다음과 같은 게리아 오류와 같은 다양한 증상으로도 나타낼 수 있습니다. _SQLSTATE\[08S01\]: 통신 링크 실패: 1047 WSREP_. MySQL 디스크 공간 부족으로 인한 오류 목록은 [클라우드 인프라의 Adobe Commerce에서 MySQL 디스크 공간 부족](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

디스크 공간 문제가 있고 New Relic 계정이 있는지 확실하지 않은 경우 [New Relic Infrastructure 모니터링 호스트 페이지](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). 여기에서 **스토리지** 탭, **차트 표시** 5개에서 20개 결과까지 표시하고 디스크 사용량 % 차트나 표에서 높은 디스크 사용에 대한 표를 확인합니다. 자세한 단계는 를 참조하십시오. [New Relic 인프라 모니터링 > 스토리지 탭]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)을 참조하십시오.

위에 설명된 증상이 있는 경우, 인노드의 상태를 확인하여 파일 번호 문제로 인해 이러한 현상이 발생하지 않는지 확인하십시오. 이렇게 하려면 CLI/Terminal에서 다음 명령을 실행합니다.\
`df -ih`

IUse% > 90%입니까?

a. 예 - 파일이 너무 많기 때문에 발생합니다. 에서 파일을 안전하게 제거하는 단계를 검토하십시오. [클라우드 인프라의 Adobe Commerce에서 디스크 공간이 부족할 때 파일을 안전하게 삭제](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). 다음으로 진행 [2단계](#step-2) 이 단계를 완료한 후. 추가 공간을 요청하려면, [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. 아니요 - 공간을 확인합니다. 실행 `df -h | grep mysql` 그런 다음 `df -h | grep tmp` CLI/터미널에서 `/tmp` 및 `/data/mysql` 디렉토리. 다음으로 진행 [3단계](#step-3).

+++

## 2단계 - 디스크 공간 확인 {#step-2}

+++**디스크 공간 사용을 확인하시겠습니까?**

파일 수를 줄이면 `df -h | grep mysql` 그런 다음 `df -h | grep tmp` CLI/터미널에서 의 디스크 공간 사용량을 `/tmp` 및 `/data/mysql`. 다음에 70% 이상 사용됨: `/tmp` 또는 `/data/mysql`?

a. 예 - 진행합니다. [3단계](#step-3).
b. 아니요 - 쿼리로 인해 사용 가능한 스토리지가 부족할 수 있습니다. 이렇게 하면 노드가 충돌하여 쿼리가 종료되고 `tmp` 파일. 의 출력 검사 `SHOW PROCESSLIST;` MySQL CLI에서 문제의 원인일 수 있는 쿼리에 대해 설명합니다. [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)추가 공간을 요청하는 중입니다.

+++

## 3단계 - 사용량이 많은 디렉토리 식별 {#step-3}

+++**70% 이상이 사용된 디렉터리는 무엇입니까?**

70% 이상이 사용된 디렉터리는 무엇입니까? `/tmp` 또는 `/data/mysql`?

>[!NOTE]
>
>기본적으로 데이터베이스 tmpdir은에 씁니다. `/tmp`. 데이터베이스 구성이 이 기본값에 있는지 확인하려면 MySQL CLI에서 다음 명령을 실행합니다. `SHOW VARIABLES LIKE "TMPDIR";` 데이터베이스 tmpdir이 계속 쓰는 경우 `/tmp`, 다음을 확인할 수 있습니다. `/tmp` 값 열에서 다음을 수행합니다.

a. `/tmp` - 다음으로 진행 [4단계](#step-4). \
b. `/data/mysql` - 다음으로 진행 [5단계](#step-5).

+++

## 4단계 - /tmp 마운트 문제 해결 가득 참 {#step-4}

+++**/tmp 마운트 문제 해결 가득 참**

[Adobe Commerce에 대한 /tmp 마운트 가득 참 문제 해결](/help/troubleshooting/miscellaneous/tmp-mount-full.md)문서를 아래로 스크롤하여 솔루션과 모범 사례를 시도해 보십시오. 그런 다음 실행 `df -h | grep mysql` 그런 다음 `df -h | grep tmp` CLI/터미널에서 의 디스크 공간 사용량을 `/tmp` 및 `/data/mysql` 디렉터리\
  70% 미만 사용

>[!NOTE]
>
>의 솔루션 [Adobe Commerce에 대한 /tmp 마운트 가득 참 문제 해결](/help/troubleshooting/miscellaneous/tmp-mount-full.md) 는 데이터베이스 tmpdir에 대한 변수를 변경하지 않은 판매자를 위해 설계되었습니다. 이 변수에는 기본적으로 `/tmp`. tmpdir 값을 변경한 경우 [Adobe Commerce에 대한 /tmp 마운트 가득 참 문제 해결](/help/troubleshooting/miscellaneous/tmp-mount-full.md) 도움이 되지 않습니다.

a. 예 - 문제를 해결했습니다. \
b. 아니요 - [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)추가 공간을 요청하는 중입니다.

+++

## 5단계 - 기본값 확인 {#step-5}

+++**기본값 확인**

데이터베이스 구성이 더 이상 원래 기본값이 아닐 수 있습니다. MySQL CLI에서 를 실행하여 데이터베이스 tmpdir 구성을 찾습니다. `SELECT @@DATADIR;`. If `/data/mysql/` 가 출력되면 데이터베이스 tmpdir이 `/data/mysql/`. 의 단계에 따라 이 디렉터리의 공간을 늘리십시오. [클라우드 인프라의 Adobe Commerce에서 MySQL 디스크 공간 부족](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). 그런 다음 실행 `df -h | grep mysql` 그런 다음 `df -h | grep tmp` CLI/터미널에서 의 디스크 공간 사용량을 `/data/mysql` 및 `/tmp`.\
  70% 미만 사용

a. 예 - 문제를 해결했습니다. \
b. 아니요 - [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)추가 공간을 요청하는 중입니다.

+++

[1단계로 돌아가기](#step-1)
