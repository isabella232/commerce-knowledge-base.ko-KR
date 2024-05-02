---
title: '''[!UICONTROL Recommendations] [!DNL JS] Adobe Commerce 버전 2.4.5로 업그레이드 후 오류 발생'
description: 이 문서에서는 Adobe Commerce으로 업그레이드한 후 (모든 배포 방법)에 [!DNL JS] 제품과 관련된 콘솔의 오류 [!UICONTROL Recommendations] 모듈.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] Adobe Commerce 버전 2.4.5로 업그레이드 후 오류 발생

이 문서에서는 Adobe Commerce으로 업그레이드한 후 (모든 배포 방법)에 [!DNL JS] 제품과 관련된 콘솔의 오류 [!UICONTROL Recommendations] 모듈/단위.

현재 향후 버전에서 이 문제를 해결할 계획이 없습니다.

## 영향을 받는 버전 및 제품

* 버전 2.4.5로 업그레이드할 때 Adobe Commerce(모든 배포 방법)

## 문제

이 문제는 상점 첫 페이지 페이지가 삭제된 일부 제품을 계속 참조하기 때문에 발생합니다 [!UICONTROL Recommendations] 홈 페이지의 모듈/단위(블록 및/또는 위젯) [!DNL CMS].

<u>재현 단계</u>:

1. Adobe Commerce 2.4.5로 업그레이드하십시오.
1. Storefront 웹 페이지에 액세스합니다.
1. 마우스를 마우스 오른쪽 단추로 클릭하고 **Inspect** 을 클릭하여 웹 브라우저에서 웹 관리자를 엽니다.
1. 다음을 클릭합니다. **[!UICONTROL Console]** 탭.
1. 리뷰 [!DNL JS] 오류.

<u>예상 결과</u>:

업그레이드 성공(아니요) [!DNL JS] 오류.

<u>실제 결과</u>:

여러 가지 유형의 [!DNL JS] 웹 브라우저 콘솔에 오류가 표시됩니다.

## 해결 방법

해결 방법으로, 모든 [!UICONTROL Recommendations] 페이지에서 사용한 장치를 제거하고 삭제된 장치를 제거합니다.
