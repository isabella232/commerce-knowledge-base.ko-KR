---
title: 'MDVA-39181: 관련 제품 규칙은 규칙에 정의되지 않은 범주의 제품을 표시합니다.'
description: MDVA-39181 패치는 관련 제품 규칙이 규칙에 정의되지 않은 범주의 제품을 표시하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39181입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181: 관련 제품 규칙에 규칙에 정의되지 않은 범주의 제품이 표시됨

MDVA-39181 패치는 관련 제품 규칙이 규칙에 정의되지 않은 범주의 제품을 표시하는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치되었습니다. 패치 ID는 MDVA-39181입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관련 제품 규칙은 규칙에 정의되지 않은 범주의 제품을 보여 줍니다.

<u>전제 조건</u>:

샘플 데이터를 설치합니다.

<u>재현 단계</u>:

1. 속성 브랜드를 만들고 **최상위 속성 집합**.
1. 선택 **조시**, **아우구스타**, 및 **잉그리드** 브랜드 키티에 추가하는 재킷 **여성** > **탑스** > **자켓 카테고리**.
1. 선택 **보몬트**, **Hyperion**, 및 **케노비** 브랜드 키티에 추가하는 재킷 **남성** > **탑스** > **재킷 범주**.
1. 관련 제품 만들기:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * 일치하는 제품:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * 표시할 제품:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. 프론트엔드에서 SKU WJ04를 열고 관련 제품을 확인하십시오.
1. 다음에서 카테고리 ID 업데이트: **여성** > **탑스** > **재킷** 이것과 다를 경우에 대비해서요

<u>예상 결과</u>:

관련 제품에는 동일한 브랜드 및 동일한 하위 카테고리의 제품만 표시됩니다.

<u>실제 결과</u>:

관련 제품은 동일한 브랜드로 표시되지만 임의의 상위 카테고리에 속합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
