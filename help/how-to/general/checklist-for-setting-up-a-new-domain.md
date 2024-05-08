---
title: 새 설정 체크리스트 [!DNL domain]
description: 다음은 신규 설정 방법에 대한 체크리스트입니다 [!DNL domain] Adobe Commerce on cloud infrastructure.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# 새 설정 체크리스트 [!DNL domain]

다음은 신규 설정 방법에 대한 체크리스트입니다 [!DNL domain] Adobe Commerce on cloud infrastructure. 새 도메인을 추가하는지 아니면 현재 도메인을 새 도메인으로 바꾸는지에 관계없이 적용됩니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 새 도메인을 설정하는 방법

### 1단계 - 다음에 대한 것입니까? [!DNL Integration, Staging], 또는 [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] 은(는) 지원되지 않습니다. 대신 이 메서드를 사용해야 합니다. [여러 웹 사이트 또는 스토어 설정: 로컬 설치 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) 사용 안내서에서 참조하십시오.
* **[!DNL Staging]**: 다음으로 이동 **2단계**.
* **[!DNL Production]**: 다음으로 이동 **3단계**.

### 2단계 - [!DNL Staging environment]: 을(를) 진행 중입니다. [!DNL Pro] 또는 [!DNL Starter]?

* **[!DNL Pro]**: **요청 제출** 에 도메인을 추가하려면 [!DNL Fastly, Nginx], 및 구성 [!DNL SSL certificate] (및 [!DNL Sendgrid domain], 필요한 경우 ). 구성이 완료되면 [업데이트 [!DNL DNS] 구성 [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>새 을(를) 추가할 수 있습니다 [!DNL domain] 끝 [!DNL Fastly] 에서 구성을 업데이트하여 직접 [!DNL Admin] 위치: **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** 에서와 같이 [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) 사용 안내서에서 참조하십시오.
>
>도메인을 추가할 수 없는 경우 다음 이유 중 하나가 원인일 수 있습니다.
>
>1. 도메인을 자체 구성된 클라우드 환경으로 마이그레이션하고 있습니다 [!DNL Fastly] 서비스. 이 경우 요청을 제출하고 도메인의 위임을 요청합니다.
>1. 도메인을 Starter에서 Pro로 마이그레이션하고 있습니다. 이 경우 추가 지원 요청을 제출합니다.

* **[!DNL Starter]**: [!DNL Custom domains] 는 스테이징 환경에서 지원되지 않습니다.

### 3단계 - [!DNL Production environment]: 을(를) 진행 중입니다. [!DNL Pro] 또는 [!DNL Starter]?

* **[!DNL Pro]**: **요청 제출** 에 도메인을 추가하려면 [!DNL Fastly, Nginx], 및 구성 [!DNL SSL certificate] (as the [!DNL Sendgrid domain], 필요한 경우 ). 구성이 완료되면 을(를) 계속합니다. **4단계**.

>[!NOTE]
>
>새 을(를) 추가할 수 있습니다 [!DNL domain] 끝 [!DNL Fastly] 에서 구성을 업데이트하여 직접 [!DNL Admin] 위치: **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) 사용 안내서에서 참조하십시오.
>
>
>도메인을 추가할 수 없는 경우 다음 이유 중 하나가 원인일 수 있습니다.
>
>1. 도메인을 온-프레미스에서 자체 구성된 클라우드 환경으로 마이그레이션하고 있습니다. [!DNL Fastly] 서비스. 이 경우 요청을 제출하고 도메인의 위임을 요청합니다.
>1. 도메인을 Starter에서 Pro로 마이그레이션하고 있습니다. 이 경우 추가 지원 요청을 제출합니다.

* **[!DNL Starter]**: 를 추가합니다. [!DNL domain] 을(를) 의 프로젝트에 **[!DNL Domains]** 탭을 선택한 다음 **요청 제출** 을(를) 제공하려면 **[!DNL ACME Challenge Key]** 대상: [!DNL SSL certificate].

### 4단계 - - 다음과 같음 [!DNL domain] 라이브?

* **예**: [업데이트 [!DNL DNS] 구성 [!UICONTROL production] 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **아니요**: [업데이트 [!DNL DNS] 구성 [!UICONTROL development] 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## 관련 읽기

* [여러 웹 사이트 또는 스토어 설정: 새로 추가 [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) 사용 안내서에서 참조하십시오.
