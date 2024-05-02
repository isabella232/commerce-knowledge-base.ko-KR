---
title: 처리량이 많은 AJAX 요청으로 인해 성능이 저하됨
description: 이 문서에서는 처리량이 많은 일부 요청으로 인해 상당한 서버 로드 및 트래픽이 발생하여 Adobe Commerce 온프레미스 또는 Adobe Commerce 기반 구조 사이트의 성능 문제에 대한 솔루션을 제공합니다.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# 처리량이 많은 AJAX 요청으로 인해 성능이 저하됨

이 문서에서는 처리량이 많은 일부 요청으로 인해 상당한 서버 로드 및 트래픽이 발생하여 Adobe Commerce 온프레미스 또는 Adobe Commerce 기반 구조 사이트의 성능 문제에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x
* Adobe Commerce 온-프레미스 2.2.x, 2.3.x

>[!NOTE]
>
>Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 버전 2.3.4에서 문제가 해결되었습니다.

### 문제

중요한 AJAX 요청과 같이 처리량이 많은 요청으로 인해 사이트 성능이 느려집니다.

### 원인

처리량이 많은 AJAX 요청에는 고객의 개인 컨텐츠와 관련된 요청이 포함됩니다.

### 솔루션

세 가지 솔루션이 있습니다.

* [버전 2.3.4로 업그레이드](https://devdocs.magento.com/cloud/project/project-upgrade.html). 현재 가능하지 않은 경우 [문제를 해결하는 패치 설치](/help/troubleshooting/known-issues-patches-attached/performance-issues-caused-by-excessive-ajax-requests.md).
* 더 가벼운 요청(캐시 요청 또는 고객의 개인 컨텐츠로 이동)을 확인하십시오.
* 요청 수를 줄입니다.

<u>더 가벼운 요청(캐시 요청 또는 고객의 개인 컨텐츠로 이동) 보장</u>

각 페이지에서 트리거되는 서드파티 AJAX 요청이 있는 경우 이러한 요청을 캐시하거나 고객의 개인 콘텐츠로 이동하려고 합니다. 판매자는 사용자 지정 AJAX 요청이 GET HTTP 메서드를 사용하여 호출되는지 확인하여 이 작업을 수행할 수 있습니다. Fastly를 통해 이러한 요청을 취소할 수 있습니다. 캐시해서는 안 되는 사용자 지정 AJAX 요청이 있는 경우 개인 콘텐츠 기능에 따라 리팩터링해야 합니다. 단계는 를 참조하십시오. [비공개 콘텐츠](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html) 개발자 설명서에서 확인할 수 있습니다.

<u>요청 수 감소</u>

* 지속 장바구니 수를 늘릴 수 있으므로 비활성화하십시오. `customer/section/load` 요청. 의 단계를 따릅니다. [지속적인 장바구니 경로](https://devdocs.magento.com/guides/v2.3/config-guide/prod/config-reference-most.html#persistent-shopping-cart-paths) 개발자 설명서에서 지속성 장바구니가 활성화되어 있는지 확인하십시오.
* 에서 콘텐츠를 다시 로드하거나 무효화해야 하는 경우 `sections.xml` 의 단계를 따릅니다. [비공개 콘텐츠: 비공개 콘텐츠 무효화](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html#invalidate-private-content) 개발자 설명서에서 확인할 수 있습니다. 다음을 사용하지 않는지 확인하십시오. `customerData.reload()` 메서드를 사용자 지정에서 직접 사용할 수 있습니다.
* 동일한 페이지에서 다른 POST AJAX 요청을 확인합니다. Google Chrome 브라우저에서 Google Chrome 개발자 도구를 엽니다. 을(를) 클릭합니다 **네트워크** 탭을 클릭한 다음 **XHR** 탭으로 설정하면 특정 페이지의 모든 AJAX 요청 목록이 표시됩니다. 그런 다음 각 요청을 클릭하고 필드의 요청 방법 이 GET 요청이어야 합니다. 참고: Google Chrome이 예로 사용되며 다른 브라우저에서도 이 작업을 수행할 수 있습니다.
* 특정 AJAX 요청인 Google 태그 관리자(GTM) 기능을 확인하십시오. 사용자는 이 AJAX을 제거하고 개인 기능으로 사용자 지정을 리팩터링하여 서버에 대한 총 요청 수를 줄일 수 있습니다.
* Adobe Commerce 배너가 활성화되어 있지만 사용되지 않는지 확인합니다. 다음을 수행해야 합니다. [Adobe Commerce 배너 출력을 비활성화하여 사이트 성능 향상](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md).

### 관련 읽기

개인 고객 콘텐츠에 대한 자세한 내용은 [비공개 콘텐츠](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=ajax%20requests) 개발자 설명서에서 확인할 수 있습니다.
