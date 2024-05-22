---
title: '[!DNL Elasticsearch] 에도 불구하고 검색 엔진으로 표시됩니다. [!DNL OpenSearch] 설치'
description: 이 문서에서는 다음과 같은 문제에 대한 솔루션을 제공합니다. [!DNL Elasticsearch] 를 설치하거나 업그레이드한 후에도 여전히 클라우드에서 Adobe Commerce에 대한 검색 엔진으로 표시됩니다. [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1f053f76ae56edc06bfe82e55210244c8ec4b8eb
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# [!DNL Elasticsearch] 에도 불구하고 검색 엔진으로 표시됩니다. [!DNL OpenSearch] 설치

이 문서에서는 다음과 같은 문제에 대한 솔루션을 제공합니다. [!DNL Elasticsearch] 를 설치하거나 업그레이드한 후에도 여전히 클라우드에서 Adobe Commerce에 대한 검색 엔진으로 표시됩니다. [!DNL OpenSearch].

## 영향을 받는 버전

cloud 2.4.3-p2 - 2.4.5-p6의 Adobe Commerce

>[!NOTE]
>
>[!DNL OpenSearch] 는 Adobe Commerce 2.4.6부터 검색 엔진으로 사용할 수 있습니다.

## 문제

[!DNL Elasticsearch] 를 설치하거나 업그레이드한 후에도 여전히 클라우드에서 Adobe Commerce에 대한 검색 엔진으로 표시됩니다. [!DNL OpenSearch].

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. 검색 엔진을 확인합니다. 표시됩니다. [!DNL Elasticsearch7].

## 원인

Adobe Commerce은 지정하기 위해 하드 코딩됨 [!DNL Elasticsearch7] 검색 엔진으로 사용됩니다.

이는 설치된 서비스 버전과 혼동하지 않습니다. 애플리케이션은 만 인식합니다. [!DNL Elasticsearch7] 검색 엔진으로 사용되지만 검색 엔진으로 사용되지 않음 [!DNL OpenSearch]를 검색하는 데 사용됩니다. [!DNL OpenSearch] 를 백엔드의 엔진으로 사용합니다.

## 솔루션

다음을 확인하려면: [!DNL OpenSearch] 이(가) 설치되었으므로 다음 명령을 실행합니다.

**방법 1**:

* 서버에서 다음 명령을 실행합니다. `curl 127.0.0.1:9200`. 반환되어야 합니다. [!DNL OpenSearch] 버전 포함.

예:

```
$ curl 127.0.0.1:9200
{
  "name" : $clusterName,
  "cluster_name" : "opensearch_stg",
  "cluster_uuid" : $clusterUuid,
  "version" : {
    "distribution" : "opensearch",
    "number" : "1.2.4",
    "build_type" : "deb",
    "build_hash" : "44ccdbaed5fe5a8b02d99a611857a671b6dd909d",
    "build_date" : "2022-11-08T09:23:45.993372Z",
    "build_snapshot" : false,
    "lucene_version" : "8.10.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

**방법 2**:

* Magento 클라우드 CLI에서 다음 명령을 사용합니다. `magento-cloud relationships -p <project_id>`. 명령을 사용한 후 다음을 찾습니다 [!DNL OpenSearch].

## 관련 읽기

[OpenSearch 서비스 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.
