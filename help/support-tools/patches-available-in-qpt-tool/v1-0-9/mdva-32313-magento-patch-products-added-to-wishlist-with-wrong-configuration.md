---
title: 'MDVA-32313 패치: 잘못된 구성으로 위시리스트에 추가된 제품'
description: MDVA-32313 패치는 구성 가능한 제품을 위시리스트에 추가할 때 잘못된 구성이 할당되어 위시리스트에 올바르게 추가할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 해결되었습니다.
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-32313 패치: 잘못된 구성으로 위시리스트에 추가된 제품

MDVA-32313 패치는 구성 가능한 제품을 위시리스트에 추가할 때 잘못된 구성이 할당되어 위시리스트에 올바르게 추가할 수 없는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10이 설치되었습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.3.0

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.3.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 고객을 만듭니다.
1. 고객 계정에 로그인합니다.
1. 다음 위치로 이동 **제품 목록** 페이지를 가리키도록 업데이트하는 중입니다.
1. 구성 가능한 제품 선택(예: *구성 가능\_1* )을 클릭하고 **제품 목록** 페이지 (**제품 페이지를 열지 마십시오.**).
1. 구성 가능한 다른 제품의 위시리스트 아이콘을 클릭합니다(예: *구성 가능\_2*)을 클릭하여 제품에서 사용할 수 있습니다.

<u>예상 결과</u>:

다음 *구성 가능\_2* 예상대로 선택한 옵션 없이 제품이 위시리스트에 추가됩니다.

<u>실제 결과</u>:

다음 *구성 가능\_2* 제품이 위시리스트에 추가되고 *구성 가능\_1* 제품.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
