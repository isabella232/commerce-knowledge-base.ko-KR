---
title: '[!DNL Admin] 로그인이 작동하지 않음 - 허용된 세션 최대 크기 초과'
description: 에 로그인하려고 할 때 문제를 해결합니다. [!DNL Admin] 패널 및 양식이 새로 고침되고 로그인할 수 없습니다.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 8718148f6d9a40c9a71484a7fbc818a626e825e1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# [!DNL Admin] 로그인이 작동하지 않음 - 허용된 세션 최대 크기 초과

이 문서에서는에 로그인하려고 할 때 대한 수정 사항을 제공합니다. [!DNL Admin] 패널은 표시되지만 양식이 새로 고침되고 로그인할 수 없습니다. 이유는 다음과 같습니다. [!DNL Admin] 세션 크기를 초과했습니다.

## 영향을 받는 버전

* Adobe Commerce 온-프레미스, [지원되는 모든 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 문제

에 로그인할 수 없습니다. [!DNL Admin]: 양식이 계속 다시 로드되기 때문입니다.

## 원인

허용된 세션 최대 크기를 초과했습니다.

## 솔루션

다음 확인: `var/log/support_report.log` 다음과 같은 오류에 대한 파일입니다.

*[2023년 7월 13일:26:09.792060+00:00] report.WARNING: 세션 크기가 260572의 허용된 세션 최대 크기를 256000. [] []
[2023년 7월 13일:26:17.056714+00:00] report.WARNING: 세션 크기가 260570의 허용된 세션 최대 크기를 256000. [][]*

이러한 오류가 표시되면 해결 방법은 다음과 같습니다.

<u>Adobe Commerce 온-프레미스</u>:
1. 늘리기 **[!UICONTROL Max Session Size in Admin]** 백엔드 구성의 값입니다. 이렇게 하려면 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. 값을 다음으로 설정 *500000* 또는 그 이상 오류에 보고된 기존 최대 크기에 따라 값을 로 설정할 수도 있습니다. *0* 세션 크기 제한이 제거됩니다.

<u>클라우드 인프라의 Adobe Commerce</u>:

(이 설정은 [!DNL Admin] 배포/작업 모드가 default 또는 developer인 경우. 그러나 클라우드 환경에서는 프로덕션 배포 모드만 허용됩니다.)

이 값을 늘리려면 터미널(SSH)에서 이 명령을 실행합니다.

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

을 보다 높게 설정할 수 있습니다. *500000* 오류에 보고된 기존 최대 크기에 따라 값을 로 설정할 수도 있습니다. *0* 세션 크기 제한을 제거합니다.

## 관련 읽기

* [세션 크기](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions) 관리 시스템 안내서에서 확인할 수 있습니다.
* [작업 모드](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode) 구성 안내서에서 참조할 수 있습니다.
* [보안 연결](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) Commerce on Cloud Infrastructure Guide를 참조하십시오.
