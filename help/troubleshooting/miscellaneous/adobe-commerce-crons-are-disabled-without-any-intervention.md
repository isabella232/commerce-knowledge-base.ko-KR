---
title: Adobe Commerce [!DNL crons] 개입 없이 비활성화됨
description: 이 문서를 사용하여 다음 위치에서 문제를 해결하십시오. [!DNL crons] 개입 없이 비활성화됩니다.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 9cd7cabc37c0f290c41f790b0fb06177c3156d48
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# 개입 없이 Adobe Commerce 크론이 비활성화됨

이 문서에서는 다음에 대한 솔루션을 제공합니다. [!DNL crons] 개입 없이 비활성화됩니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모두 [지원되는 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## 문제

사용자 [!DNL crons] 배포 후 비활성화됩니다.

<u>재현 단계</u>:

배포.

<u>예상 결과</u>:

사용자 [!DNL crons] 실행 중입니다.

<u>실제 결과</u>:

사용자 [!DNL crons] 배포 후 비활성화됩니다.

## 원인

문제 [!DNL OPcache] 설정.

## 솔루션

업그레이드 [!DNL ECE Tools] 최신 버전으로 [2002.1.13](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html#v2002113).

## 관련 읽기

* [느린 성능, 느리고 긴 실행 [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) 을 참조하십시오.
* [[!DNL Cron] 작업은 다른 그룹의 작업을 잠급니다.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) 을 참조하십시오.
* [[!DNL Cron] 작업이 &quot;실행 중&quot; 상태에서 중단됨](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) 을 참조하십시오.
