---
title: 'MDVA-43601: 트리거가 전체 색인 재지정 후 "catalogule_product_price" 테이블에서 제거됩니다.'
description: MDVA-43601 패치는 'catalogrule_rule' 또는 'catalogrule_product'의 전체 색인 변경 후 트리거가 'catalogrule_product_price' 테이블에서 제거되는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43601입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601: 트리거는 전체 색인 재지정 후 &quot;catalogrule_product_price&quot; 테이블에서 제거됩니다.

MDVA-43601 패치는에서 트리거가 제거되는 문제를 해결합니다. `catalogrule_product_price` 전체 색인 재지정 후 표 `catalogrule_rule` 또는 `catalogrule_product`. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13이 설치되었습니다. 패치 ID는 MDVA-43601입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

트리거가에서 제거됨 `catalogrule_product_price` 전체 색인 재지정 후 표 `catalogrule_rule` 또는 `catalogrule_product`.

<u>재현 단계</u>:

1. 모든 인덱서를 다음으로 설정 *예약별 업데이트*.
1. 다음에 대해 생성된 트리거 확인 `catalogrule_product_price` 다음 SQL 요청을 실행하여 테이블을 생성합니다.

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. 수동으로 색인 재지정 `catalogrule_rule` 또는 `catalogrule_product` 다음 명령을 실행하여 다음을 수행합니다. `bin/magento indexer:reindex catalogrule_rule`
1. 의 트리거 확인 `catalogrule_product_price` 다시 한 번.

<u>예상 결과</u>:

트리거 위치 `catalogrule_product_price` 전체 색인 재지정 후 테이블이 유지됩니다.

<u>실제 결과</u>:

에 대한 트리거를 찾을 수 없음 `catalogrule_product_price` 테이블.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
