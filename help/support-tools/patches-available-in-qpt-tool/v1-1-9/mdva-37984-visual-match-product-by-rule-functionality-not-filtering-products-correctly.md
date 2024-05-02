---
title: 'MDVA-37984: 스테이징 업데이트를 적용할 때 시각적 머천다이저가 올바르게 작동하지 않음'
description: MDVA-37984 패치는 스테이징 업데이트가 적용될 때 시각적 머천다이저의 "제품별 일치" 기능이 제품을 제대로 필터링하지 못하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37984입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984: 스테이징 업데이트를 적용할 때 시각적 머천다이저가 올바르게 작동하지 않음

MDVA-37984 패치는 스테이징 업데이트가 적용될 때 시각적 머천다이저의 &quot;제품별 일치&quot; 기능이 제품을 제대로 필터링하지 못하는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9가 설치되었습니다. 패치 ID는 MDVA-37984입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

시각적 머천다이저의 &quot;규칙별 제품 일치&quot; 기능은 스테이징 업데이트가 적용될 때 제품을 올바르게 필터링하지 않습니다.

<u>재현 단계</u>:

1. 기존 제품에 대한 일정 업데이트를 만듭니다.
   * 다음에 대해 다른 값 설정 `entity_id` 및 `row_id`.
1. 구성 가능한 새 제품을 만든 다음 간단한 제품을 만듭니다(따라서 새 제품 `entity_id` 및 `row_ids` 도 다릅니다.)
   * 문제를 더 쉽게 복제할 수 있도록 단순 제품에 대해 구별 가능한 수량 값(예: 5000)을 설정합니다.
1. 범주로 이동 > **범주 내 제품** 및 활성화 **규칙별 제품 일치**.
1. 이제 속성으로 &quot;Quantity&quot;, 연산자로 &quot;Greater&quot;, 값으로 &quot;4500&quot;을 선택합니다.
1. 클릭 **저장**.

<u>예상 결과</u>:

새로 만든 구성 가능한 제품이 나열됩니다.

<u>실제 결과</u>:

새로 만든 구성 가능한 제품이 나열되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
