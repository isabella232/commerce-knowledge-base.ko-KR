---
title: "MDVA-39935: GraphQL은 웹 사이트 수준에서 비활성화된 구성 가능한 하위 제품을 반환합니다."
description: MDVA-39935 Adobe Commerce 패치는 GraphQL이 웹 사이트 수준에서 비활성화된 구성 가능한 하위 제품을 반환하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39935입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 45bd6bd9-3572-4477-a689-d6b952a3290a
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39935: GraphQL은 웹 사이트 수준에서 비활성화된 구성 가능한 하위 제품을 반환합니다.

MDVA-39935 Adobe Commerce 패치는 GraphQL이 웹 사이트 수준에서 비활성화된 구성 가능한 하위 제품을 반환하는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2가 설치되었습니다. 패치 ID는 MDVA-39935입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL은 구성 가능한 하위 제품이 웹 사이트 수준에서 비활성화된 후에도 이를 반환합니다.

<u>재현 단계</u>:

1. 아래에서 품절 제품 표시 옵션을 활성화합니다. **저장** > **구성** > **카탈로그** > **인벤토리** > **스톡 옵션** > **품절 제품 표시** > **예**.
1. 모두 선택 **구성 가능한 제품** 2개 이상 있는 것 **단순 제품**.
1. 사용 안 함 **단순 제품** 및 저장 **구성 가능한 제품**.
1. 가져오기 **구성 가능한 제품** GraphQL을 사용하는 데이터입니다.

<pre>
  <code class="language-graphql">
{
  products(filter: { sku: { eq: "cp1" } }) {
    items {
      __typename
      name
      sku
      ... on ConfigurableProduct {
        variants {
          product {
            __typename
            name
            sku
            color
            stock_status
          }
        }
      }
    }
  }
}
</code>
</pre>

<u>예상 결과</u>:

비활성화된 제품은 변형 결과에 표시되지 않습니다.

<u>실제 결과</u>:

비활성화된 제품 데이터를 변형 결과로 가져옵니다.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

Adobe Commerce용 품질 패치에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션.
