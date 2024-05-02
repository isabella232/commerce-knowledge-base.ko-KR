---
title: "파일을 삭제할 수 없습니다. 경고! 연결 해제: 파일 또는 디렉토리 오류가 없는 [!DNL Admin]"
description: 이 문서에서는 *파일을 삭제할 수 없는 문제에 대한 해결 방법을 제공합니다. 경고!unlink 해당 파일 또는 디렉토리 오류가 없습니다.* [!DNL Admin] 다음을 수행하는 경우 [!DNL Javascript/CSS] 플러시.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *파일을 삭제할 수 없습니다. 경고!unlink: 해당 파일 또는 디렉터리 오류가 없습니다.* 다음에서 [!DNL Admin]

이 문서에서는 오류가 표시되는 문제에 대한 해결 방법을 제공합니다 *파일을 삭제할 수 없습니다. 경고!unlink: 해당 파일 또는 디렉터리 오류가 없습니다.* 다음에서 [!DNL Commerce Admin] 다음을 수행하는 경우 [!DNL JavaScript/CSS] 플러시.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.0 - 2.4.6, 모든 배포 방법

## 문제

다음 작업을 수행하면 오류가 발생합니다. [!DNL JS/CSS] 플러시:

*&quot;/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b&quot; 파일은 삭제할 수 없습니다. 경고!unlink(/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b): 해당 파일 또는 디렉터리가 없습니다.*

또는:에 위의 오류가 표시됩니다. [!DNL Admin], 및/또는 의 유사한 오류 [!DNL New Relic] 배포 로그에서 참조할 수 있습니다.

또는: 고급 보고에 액세스할 수 없으며 analytics_collect_data cron 작업이 다음 오류로 실패합니다.

*&quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0&quot; 파일을 삭제할 수 없습니다. 경고!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0): 해당 파일 또는 디렉터리가 없습니다.*

<u>재현 단계:</u>

방법 1:

1. 에 로그인합니다 [!DNL Admin].
1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. 클릭 **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

방법 2:

1. 에 로그인합니다 [!DNL Admin].
1. 다음으로 이동 **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. 변경 내용 [!UICONTROL Base URL] 또는 [!UICONTROL Base URL (Secure)].
1. 클릭 **[!UICONTROL Save Config]**.

## 솔루션

Adobe Commerce on Cloud infrastructure를 사용하고 있고 [!DNL magento/magento-cloud-patches] 1.0.22가 설치되었으며 패치가 포함되어 있으므로 ACSD-50165을 별도로 설치할 필요가 없습니다.

Adobe Commerce on Cloud infrastructure: Commerce용 클라우드 패치를 1.0.22로 업그레이드(**이상**) 이 수정 사항을 포함하는 [Commerce용 클라우드 패치](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce 온-프레미스: 다음을 사용하여 ACSD-50165 적용 [품질 패치 도구 > 사용](/docs/commerce-operations/tools/quality-patches-tool/usage.html). ACSD-50165 패치에는 [!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## 관련 읽기

* [[!DNL Quality Patches Tool] > 릴리스 노트](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) Commerce 툴 안내서에서 확인할 수 있습니다.
* [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) Commerce 툴 안내서에서 확인할 수 있습니다.
