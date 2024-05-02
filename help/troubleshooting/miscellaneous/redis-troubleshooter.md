---
title: Adobe Commerce의 Redis 문제 해결사
description: 이 문서는 Redis에 문제가 있는 Adobe Commerce 온-프레미스 및 Adobe Commerce 온-클라우드 인프라 가맹점을 위한 문제 해결 도구입니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다. 증상 및 구성에 따라 문제 해결사가 버전 및 메모리 문제를 해결하고 성능을 최적화하는 방법에 대해 설명합니다.
exl-id: 241abcfd-33b8-449b-b385-32950bd26320
feature: Services, Support
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Adobe Commerce의 Redis 문제 해결사

이 문서는 Redis에 문제가 있는 Adobe Commerce 온-프레미스 및 Adobe Commerce 온-클라우드 인프라 가맹점을 위한 문제 해결 도구입니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다. 증상에 따라 문제 해결사가 버전 및 메모리 문제를 해결하고 성능을 최적화하는 방법에 대해 설명합니다.

## 1단계 - Redis 문제 {#step-1}

+++레디스 문제?

a. 예 - 진행합니다. [2단계](#step2)</a>.

b. 아니요 - (으)로 돌아가기 [support.magento.com](https://support.magento.com/hc/en-us) 관련 문제 해결 문서를 검색합니다.

+++

## 2단계 - 설치된 Redis 패치 확인 {#step-2}

+++현재 설치된 Redis 패치

a. 예 - 진행합니다. [3단계](#step3)</a>.

b. 아니요 - 최신 버전의 패키지가 있는지 확인합니다. `magento-cloud-patches` 설치됨. 이 패키지에는 Redis에 필요한 패치가 있습니다. 액세스하려면 다음으로 이동하십시오. [GitHub 자석 클라우드 패치](https://github.com/magento/magento-cloud-patches/).

+++

## 3단계 - Redis 버전 지원 확인 {#step-3}

+++Redis 버전 3.2 또는 5.0에서?

CLI에서 다음 명령을 실행하여 확인합니다. Pro 또는 스테이징: `$ redis-cli -p %port-number% info | grep redis_version`, 여기서 `%port-number%` 는 포트 번호이며, 다음에서 찾을 수 있습니다. `app/etc/env.php` 또는 다음 명령 중 하나를 실행하여 파일을 복제합니다. `$ vendor/bin/ece-tools env:config:show | grep -i redis -A 3` 또는 `$ cat app/etc/env.php | grep redis -A 3` 시작 또는 통합: `$ redis-cli -h 'redis.internal' info | grep redis_version`

a. 예 - 진행합니다. [4단계](#step4).

b. 아니요 - Adobe Commerce은 Redis 버전 3.2 및 5.0을 지원합니다. 클라우드 인프라 2.3.3 이상에서 Adobe Commerce을 실행하는 경우 Redis 5로 업그레이드하는 것이 좋습니다. 클라우드 인프라의 Adobe Commerce Pro 계획 아키텍처, 통합 및 시작 환경(마스터 분기 포함)에 대한 설정 단계는 다음을 참조하십시오. [클라우드 인프라의 Adobe Commerce > Redis 서비스 설정](https://devdocs.magento.com/cloud/project/services-redis.html)</a> 개발자 설명서에서 확인할 수 있습니다. **다음을 수행해야 합니다 [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Pro 아키텍처 프로덕션 및 스테이징 환경에서 서비스 구성을 변경합니다. 또한 Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.5+의 경우 확장된 Redis 캐시 구현을 권장합니다. 이러한 유형의 Redis 캐시 구현에서는 각 Adobe Commerce 요청에서 수행되는 Redis에 대한 쿼리 수를 최소화하는 개선 사항을 제공합니다. 단계는 를 참조하십시오. [확장된 Redis 캐시 구현 Adobe Commerce 2.3.5+](https://support.magento.com/hc/en-us/articles/360049292532) 을 참조하십시오. 기타 모든 Adobe Commerce 사용자의 경우 다음을 참조하십시오. [Adobe Commerce Configuration Guide > Configure Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/config-redis.html) 개발자 설명서에서 절차를 참조하십시오.

+++

## 4단계 - 최신 버전의 ECE-Tools 확인 {#step-4}

+++최신 버전의 [ECE 도구 > v2002.1.1](https://github.com/magento/ece-tools/releases)?

CLI/Terminal에서 명령을 실행하여 사용 중인 버전을 확인합니다. `$php vendor/bin/composer info magento/ece-tools`.

a. 예 - 진행합니다. [5단계](#step5).

b. 아니요 - [ECE-Tools 업그레이드](https://devdocs.magento.com/cloud/project/ece-tools-update.html) 최신 릴리스로 이동합니다.

+++

## 5단계 - 네트워크 트래픽 평가 {#step-5}

+++앱과 Redis 간에 네트워크 트래픽이 많습니까?

a. 예 - 다음을 시도해 보십시오. 분할되지 않은 아키텍처의 경우 [보조 연결](/help/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.md) 를 사용합니다. 분할 아키텍처의 경우 [L2 캐시를 활성화해야 합니다.](https://devdocs.magento.com/guides/v2.4/config-guide/cache/two-level-cache.html).

b. 아니요 - 다음을 통해 L2 캐시 구성 [Redis 백엔드 업데이트 중](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend). 다음으로 진행 [6단계](#step6).

+++

## 6단계 - 사이트 속도 확인 {#step-6}

+++L2 캐시를 활성화한 후에도 사이트가 여전히 느리게 작동합니까?

a. 예 - 임시 디렉토리 확인 `/dev/shm` 공간을 늘려야 하는지 알아봅니다. 공간이 더 필요하시면, [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
b. 아니요 - L2 캐시를 활성화하면 Redis 문제가 해결된 것으로 보입니다.

+++

[1단계로 돌아가기](#step-1)
