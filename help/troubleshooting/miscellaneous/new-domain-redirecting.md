---
title: 새 도메인이 기본 도메인으로 리디렉션됩니다.
description: 이 문서에서는 새 도메인이 기존 또는 다른 환경의 기본 도메인으로 리디렉션되는 문제에 대한 수정 사항을 제공합니다.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# 새 도메인이 기본 도메인으로 리디렉션됩니다.

이 문서에서는 새 도메인이 기존 또는 다른 환경의 기본 도메인으로 리디렉션되는 문제에 대한 수정 사항을 제공합니다.

## 영향을 받는 제품 및 버전

* cloud pro 인프라의 Adobe Commerce(모든 버전)

## 문제

새 도메인이 현재 환경의 기본 도메인 또는 다른 환경의 기본 도메인으로 리디렉션됩니다.

## 원인

새 도메인을 추가하거나 잘못된 도메인을 추가한 후 변수가 업데이트되지 않는 경우 발생합니다 [!DNL Fastly] 서비스가 환경에 구성되었습니다.

## 솔루션

1. 도메인이 동일한 환경 내에서 리디렉션되는 경우 다음을 구성했는지 확인합니다. [변수](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables).
1. 도메인이 다른 환경으로 리디렉션되는 경우 올바르게 구성했는지 확인합니다 [!DNL Fastly] 다음 명령을 실행하여 서비스를 생성합니다. `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>다음을 찾을 수 있습니다. [!DNL Fastly] 각 환경(스테이징/프로덕션)에 로그인하고 를 확인하여 API 자격 증명 `/mnt/shared/fastly_tokens.txt` 파일. 자세한 내용은 [구성 [!DNL Fastly] 서비스](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) Commerce on Cloud Infrastructure Guide를 참조하십시오.

위의 구성이 모두 올바른 경우 지원 티켓을 제출합니다.

## 관련 읽기

* [새 도메인 설정을 위한 체크리스트](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html) 을 참조하십시오.
