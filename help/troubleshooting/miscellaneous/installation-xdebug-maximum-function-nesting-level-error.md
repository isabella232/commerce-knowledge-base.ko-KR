---
title: 설치 xdebug 최대 함수 중첩 수준 오류
description: 이 문서에서는 설치하는 동안 xdebug 최대 함수 중첩 수준 오류를 수정합니다.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# 설치 xdebug 최대 함수 중첩 수준 오류

이 문서에서는 설치하는 동안 xdebug 최대 함수 중첩 수준 오류를 수정합니다.

## 세부 사항

Adobe Commerce 설치 중에 다음과 유사한 메시지가 표시됩니다.

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

를 사용하지 않는 것이 좋습니다 `xdebug` 프로덕션 환경에서!

## 솔루션

에 대해 알려진 문제 있음 `xdebug` 이는 Adobe Commerce 설치 또는 설치 후 상점 또는 Commerce 관리자에 대한 액세스에 영향을 줄 수 있습니다.

자세한 내용은 [xdebug의 알려진 문제](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md) 을 참조하십시오.
