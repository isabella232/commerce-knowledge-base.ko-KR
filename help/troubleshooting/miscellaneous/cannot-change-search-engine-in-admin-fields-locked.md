---
title: '''app/etc/env.php''에서 검색 엔진을 변경할 수 없음'
description: 이 문서에서는 Commerce 관리자의 검색 엔진을 변경하려고 하지만 필드가 잠겨 있는 문제에 대한 해결 방법을 제공합니다.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# 에서 검색 엔진을 변경할 수 없음 `app/etc/env.php`

이 문서는에서 검색 엔진 구성을 제거하려고 하는 문제에 대한 해결 방법을 제공합니다. `app/etc/env.php` 파일을 다시 배포하면 구성이 이전 설정으로 되돌아가거나 로 변경됩니다. [!DNL OpenSearch] 기본적으로.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, [지원되는 모든 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 문제

Commerce 관리에서 검색 엔진을 변경하려고 하지만 필드가 잠겨 있습니다.

## 원인

검색 엔진 구성이 `app/etc/env.php` 파일 또는 검색 엔진이 `.magento.env.yaml` 파일.

## 솔루션

1. 다음 확인: `.magento.env.yaml` 배포 단계 아래에 파일을 만들고 `SEARCH_CONFIGURATION` 변수가 구성되었습니다. 예:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. 다음  `SEARCH_CONFIGURATION` 변수가 있습니까? 없는 경우 검색 엔진 구성이에 대해 잠겨 있습니다. [!DNL OpenSearch] 기본적으로. 구성을 변경하려면 변수를에 추가해야 합니다 `.magento.env.yaml` 검색 엔진에 적절한 값이 있는 파일입니다. 다음과 같은 경우 `SEARCH_CONFIGURATION` 변수가 있고 엔진을 수정하려면 의 엔진 기존 값을 바꿉니다. `.magento.env.yaml`. 가능한/알려진 값: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic], 및 [!DNL amasty_elastic_opensearch].
1. 인스턴스를 재배포합니다.
1. 관리자의 검색 엔진 필드는 잠겨 있지만 지정한 값으로 업데이트되어야 합니다.

## 관련 읽기

* [Commerce 관리자의 잠긴 필드](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md) Commerce on Cloud Infrastructure 안내서에서 확인할 수 있습니다.
