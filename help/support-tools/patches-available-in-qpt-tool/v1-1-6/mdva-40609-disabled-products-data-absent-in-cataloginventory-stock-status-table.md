---
title: 'MDVA-40609: 비활성화된 제품 데이터가 cataloginventory_stock_status 테이블에 없음'
description: MDVA-40609 패치는 잘못된 제품 수량을 표시하는 'cataloginventory_stock_status' 색인 테이블에 비활성화된 제품 데이터가 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40609입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609: 비활성화된 제품 데이터가 cataloginventory_stock_status 테이블에 없음

MDVA-40609 패치는에서 비활성화된 제품 데이터가 표시되지 않는 문제를 해결합니다. `cataloginventory_stock_status` 잘못된 제품 수량을 표시하는 색인 테이블. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6이 설치되었습니다. 패치 ID는 MDVA-40609입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

비활성화된 제품 데이터가에 표시되지 않음 `cataloginventory_stock_status` 잘못된 제품 수량을 표시하는 색인 테이블.

<u>전제 조건</u>:

인벤토리 모듈이 설치되었습니다.

<u>재현 단계</u>:

1. 스토어 및 스토어 조회수를 제공하는 웹 사이트 두 개를 설정합니다.
1. 추가 소스 및 재고를 생성합니다.
1. 간단한 제품 추가:
   * 제품 사용 설정 *아니요*.
   * 출처 품목 상태 = 재고 및 수량이 0보다 큰 두 출처를 지정합니다.
1. 제품을 저장합니다.
1. 다음 확인: **제품 판매 가능 수량** 탭.

<u>예상 결과</u>:

두 주식 모두 0보다 큰 값을 입력했습니다.

<u>실제 결과</u>:

하나의 스톡 값은 0입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션.
