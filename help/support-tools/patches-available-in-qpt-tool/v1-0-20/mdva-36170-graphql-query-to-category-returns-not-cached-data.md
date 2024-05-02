---
title: 'MDVA-36170: 범주에 대한 GraphQL 쿼리가 캐시되지 않은 데이터를 반환함'
description: MDVA-36170 패치는 GraphQL 쿼리의 결과가 캐시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-36170입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 6249b751-4b71-4833-ab86-ded615d648a8
feature: Cache, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-36170: 범주에 대한 GraphQL 쿼리가 캐시되지 않은 데이터를 반환합니다.

MDVA-36170 패치는 GraphQL 쿼리의 결과가 캐시되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치되어 있습니다. 패치 ID는 MDVA-36170입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.3.6

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.1 - 2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL 쿼리의 결과가 캐시되지 않는 문제를 수정합니다.

<u>재현 단계</u>:

판매자는 GraphQL 캐싱에 GET 방법을 사용하고 있지만 캐시된 데이터를 가져오지 않습니다.

<pre>https://magento_url/graphql?query={ products(filter: {category_id: {eq: "2"}}, pageSize: 2000, currentPage: 1, sort: {position: ASC}) { items { sku id name description { html } url_key specifications image { label gallery_url } __typename quantity_in small_image { gallery_url label } product_price_range { maximum_price { final_price { value } } minimum_price { final_price { value } } } } } } .. on ConfigurableProduct { variables{ attributes{ code label value_index } product{ sku_quantity_in } } } } } } } } }}</pre>

<u>예상 결과</u>:

데이터가 캐시됩니다.

<u>실제 결과</u>:

데이터가 캐시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
