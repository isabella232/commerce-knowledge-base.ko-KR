---
title: 으로 폴백 [!DNL Elasticsearch7] 검색 엔진이 다음으로 설정된 경우 [!DNL Opensearch]
description: 이 문서에서는 *로 폴백되는 경우 문제에 대한 해결 방법을 제공합니다. [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# 으로 폴백 [!DNL Elasticsearch7] 검색 엔진이 다음으로 설정된 경우 [!DNL Opensearch]

이 문서에서는 다음과 같은 경우에 발생하는 문제에 대한 해결 방법을 제공합니다. *으로 폴백[!DNL Elasticsearch7]* 검색 엔진이 (으)로 설정된 경우 오류가 발생합니다. [!DNL OpenSearch] Adobe Commerce.

## 영향을 받는 버전

클라우드 인프라의 Adobe Commerce 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] 는 Adobe Commerce 2.4.6부터 검색 엔진으로 사용할 수 있습니다.

## 문제

을(를) 설정했습니다. **검색 엔진** 끝 **[!DNL OpenSearch]**, 그러나 다음에서 이 유형의 오류 참조: `var/log/support_report.log` 파일:

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>재현 단계</u>:

1. 다음을 확인합니다. [!DNL OpenSearch] 은(는) 다음 명령을 실행하여 설치됩니다. `curl 127.0.0.1:9200`<br>
다음을 나타내는 경우 *1.2.4*, 그런 다음 [!DNL OpenSearch] 이(가) 이미 설치되어 있습니다.
1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. 검색 엔진을 확인합니다. 표시됩니다. [!DNL Elasticsearch7].

## 원인

버전이 를 지원하더라도 [!DNL OpenSearch], 애플리케이션은 인식/수락만 합니다. [!DNL Elasticsearch7] 검색 엔진으로 사용됩니다.

Adobe Commerce 버전 2.4.6부터 애플리케이션이 를 허용하도록 업데이트되었습니다. [!DNL OpenSearch] 을 검색 엔진으로 선택합니다.
로 이동하면 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** 비클라우드 환경에서는 다음과같이 이 옵션을 변경할 수 있습니다. **솔루션** 아래요.
(참고: 클라우드 환경에서는 검색 엔진이 `app/etc/env.php` file.)

## 솔루션

업데이트 `SEARCH_CONFIGURATION` 의 변수 `.magento.env.yaml` 파일을 참조하고 **검색 엔진** 이(가) (으)로 설정됨 *[!DNL elasticsearch7]*.

## 관련 읽기

[OpenSearch 서비스 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.
