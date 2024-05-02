---
title: 'MDVA-40401: 주문 실패 후 쿠폰 사용 값 변경'
description: MDVA-40401 패치는 주문 실패 후에도 쿠폰 사용 값이 변경되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40401입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: c497ee84-9c20-4c75-ad3a-3b71f699acbf
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40401: 주문 실패 후 쿠폰 사용 값 변경

MDVA-40401 패치는 주문 실패 후에도 쿠폰 사용 값이 변경되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4가 설치되었습니다. 패치 ID는 MDVA-40401입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자는 실패한 순서로 쿠폰을 사용한 후에는 다시 적용할 수 없습니다.

<u>재현 단계</u>:

1. 자동 생성된 쿠폰으로 장바구니 규칙을 만듭니다.
1. 장바구니에 제품을 추가하고 쿠폰을 적용합니다.
1. 다음으로 이동 **체크아웃**.
1. 주문하기 전에 추가된 제품을 &quot;재고 부족&quot;으로 만듭니다.
1. 다음 항목을 얻어야 합니다. *품절* 오류.
1. 크론 실행
1. 장바구니로 이동하여 해당 제품을 제거합니다.
1. 다른 상품을 추가하시고 쿠폰을 적용하세요.

<u>예상 결과</u>:

쿠폰 코드는 이전 주문이 들어가지 않아 성공적으로 적용되어야 합니다.

<u>실제 결과</u>:

You get a *쿠폰 코드가 잘못되었습니다.* 오류.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션.
