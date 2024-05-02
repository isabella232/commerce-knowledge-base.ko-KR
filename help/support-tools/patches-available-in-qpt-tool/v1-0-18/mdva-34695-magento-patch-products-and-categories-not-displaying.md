---
title: 'MDVA-34695: 제품 및 범주가 표시되지 않음'
description: MDVA-34695 패치는 관리자의 카테고리 그리드에 제품 및 카테고리가 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-34695입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
exl-id: 0c2e50c1-648b-480a-a768-72af721950d8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-34695: 제품 및 범주가 표시되지 않음

MDVA-34695 패치는 관리자의 카테고리 그리드에 제품 및 카테고리가 표시되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치되었습니다. 패치 ID는 MDVA-34695입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.3.4

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.0-2.4.0-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

음수 값 `children_count` 범주를 삭제한 후 데이터베이스에 나타납니다.

<u>재현 단계</u>:

1. 관리 백엔드에 로그인합니다.
1. 다음으로 이동 **카탈로그 > 범주**.
1. 클릭 **하위 범주 추가**.
1. 설정 **카테고리 이름** = *상위 1*&#x200B;를 클릭한 다음 저장 을 클릭합니다.
1. 클릭 **하위 범주 추가**.
1. 설정 **카테고리 이름** = *하위 1*&#x200B;를 클릭한 다음 저장 을 클릭합니다.
1. 클릭 **하위 범주 추가**.
1. 설정 **카테고리 이름** = *하위 2*&#x200B;를 클릭한 다음 저장 을 클릭합니다.
1. 클릭 **하위 범주 추가**.
1. 설정 **카테고리 이름** = *하위 3*&#x200B;를 클릭한 다음 저장 을 클릭합니다. 이 시점에서 이 범주의 레벨은 = 입니다. *5*.
1. 을(를) 클릭합니다 **하위 1** 범주.
1. 범주를 삭제합니다.

<u>예상 결과</u>:

카테고리 그리드는 예상대로 제품 및 카테고리를 표시합니다.

<u>실제 결과</u>:

카테고리 그리드가 비어 있습니다. 다음 확인: `catalog_category_entity` 데이터베이스의 테이블입니다. 참고: `children_count` 부정적으로 변했습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션.
