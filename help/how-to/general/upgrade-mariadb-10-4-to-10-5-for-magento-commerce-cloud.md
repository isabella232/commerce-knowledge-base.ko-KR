---
title: 클라우드에서 Adobe Commerce용 MariaDB 10.4를 10.5로 업그레이드
description: MariaDB 10.4는 2024년 6월 18일에 지원이 종료됩니다. 이 문서에서는 클라우드 인프라에서 Adobe Commerce을 계속 사용하기 위해 MariaDB를 10.4에서 10.5로 업그레이드하는 방법에 대해 설명합니다.
feature: Best Practices, Cloud
source-git-commit: 401a36722b3336b47dd76bb12ace34f0bf55b8e6
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# 클라우드에서 Adobe Commerce용 MariaDB 10.4를 10.5로 업그레이드

MariaDB는 Adobe Commerce에서 사용되는 엔터프라이즈 오픈 소스 데이터베이스입니다.

MariaDB 10.4는에 대한 지원 종료 [2024년 6월 18일](https://endoflife.date/mariadb). 지원되지 않는 버전의 MariaDB를 사용하는 경우 더 이상 PCI를 준수하지 않습니다. 이 문서에서는 클라우드 인프라에서 Adobe Commerce을 계속 사용하기 위해 MariaDB 10.4에서 10.5로 업그레이드하는 방법에 대해 설명합니다.

>[!NOTE]
>
>MariaDB 10.4는 EOL(수명 종료)에 도달하므로 현재 Adobe Commerce 버전에서 더 이상 지원되지 않습니다. EOL 후 30일 이내에 EOL 버전을 사용하지 않는 것이 좋습니다.

## 영향을 받는 제품 및 버전

* 모든 Adobe Commerce 온-프레미스 및 클라우드 인프라 2.4.4 및 2.4.5

## 솔루션

MariaDB 10.5와의 호환성을 보장하기 위해 2024년 6월 11일에 출시되는 새로운 보안 전용 패치(2.4.4-p9 또는 2.4.5-p8)를 채택하십시오. 그런 다음 아래 단계에 따라 MariaDB 10.4에서 10.5로 업그레이드하십시오.

### 클라우드 배포를 위한 업그레이드 단계

1. 만들기 [ECE-Tools DB 백업 명령을 사용한 DB 백업](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). 테이블/행을 업데이트하는 동안 문제가 발생할 경우 2단계와 3단계 전에 이 백업을 수행해야 합니다.
1. [모든 컴팩트 테이블을 확인하고 다이내믹 테이블로 변환](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade). 이 단계는 데이터베이스 업그레이드 중에 발생할 수 있는 데이터 손실을 방지하기 위해 필요합니다.
1. MYISAM 테이블을 확인합니다. 다음을 수행해야 합니다. [모든 MyISAM 테이블을 InnoD로 변환](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud).
1. 데이터베이스 테이블 및 행을 준비한 후(앞의 두 단계) [ECE-Tools DB 백업 명령을 사용한 DB 백업](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [지원 티켓 열기](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) mariaDB 10.4에서 10.5로 업그레이드 일정을 예약하려면 다음을 수행하십시오. 티켓에 DB를 업그레이드하려는 날짜와 시간을 자세히 입력합니다. 지원 팀은 48시간 전에 통보해야 하며, 상인의 개발 팀은 이용할 수 있어야 합니다. 업그레이드에 대한 시간 및 날짜가 합의되면 다음을 수행합니다.
   1. 사이트를 유지 관리 모드로 전환하고 크론과 같은 DB 활동을 중지합니다.
   1. 만들기 [ECE-Tools DB 백업 명령을 사용한 DB 백업](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. 지원 티켓을 통해 백업을 완료했음을 지원 담당자에게 알립니다. 티켓을 보고 추적하는 단계를 얻으려면 다음을 참조하십시오. [Adobe Commerce 도움말 센터 사용 안내서: 티켓 추적](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) 을 참조하십시오.
   1. 그런 다음 Adobe Commerce 지원 팀이 MariaDB 업그레이드 프로세스를 시작합니다. 위의 모든 단계를 수행했으며 데이터베이스가 평균 크기인 경우 프로세스는 약 1시간이 소요됩니다. 더 큰 DB는 시간이 더 오래 걸립니다. 업그레이드가 완료되면 티켓을 통해 안내를 받게 됩니다.
1. 유지 관리 모드를 비활성화합니다. 을(를) 참조하십시오 [유지 관리 모드 활성화 또는 비활성화](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

* [DB 업그레이드 모범 사례 안내서](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites) 온-프레미스 배포용
* [클라우드에서 Adobe Commerce용 MariaDB 10.0을 10.2로 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud) 을 참조하십시오.
* [Adobe Commerce 라이프사이클 정책](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) 개발자 설명서에서 확인할 수 있습니다.
