---
title: '오류: 클라우드 인프라의 Adobe Commerce에서 준비 작업 실패'
description: '이 문서는 페이지 캐시가 준비 중이고 오류로 인해 실패할 경우에 대한 솔루션을 제공합니다.'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# ERROR: 클라우드 인프라의 Adobe Commerce에서 준비에 실패했습니다.

이 문서에서는 페이지 캐시가 준비되고 오류와 함께 실패하는 경우에 대한 솔루션을 제공합니다.

*ERROR: 예열 실패:`<website link>`*

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모두 [지원되는 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 문제

캐시 준비 실패.

<u>재현 단계</u>:

캐시 준비 작업을 시작합니다.

<u>예상 결과</u>:

페이지 또는 전체 사이트가 로드됩니다.

<u>실제 결과</u>:

사이트를 사용할 수 없거나 응답 시간이 너무 깁니다. *ERROR: 예열 실패:`<website link>`*

## 원인

HTTP 액세스 제어를 사용하도록 설정한 경우 캐시 미리 보기가 작동하지 않습니다.

## 솔루션

액세스 제어가 활성화되어 있지 않은지 확인합니다. 특정 분기/환경으로 이동한 다음 **설정** 아이콘을 클릭하고 **HTTP 액세스 제어** 설정 - 이 시나리오에서는 캐시 예열을 수행할 수 없으며 액세스 제어를 사용하지 않도록 설정해야 합니다.

## 관련 읽기

* [Adobe Commerce 사용 안내서 > 전체 페이지 캐시](https://docs.magento.com/user-guide/system/cache-full-page.html) 사용 안내서에서 참조하십시오.
* [캐시 준비 및 Adobe Commerce에서 사이트를 사용할 수 없음](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) 을 참조하십시오.
