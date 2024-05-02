---
title: 'MDVA-31021: 제품 옵션이 많은 경우 가져오기 및 내보내기 속도가 느림'
description: MDVA-31021 패치는 많은 제품 옵션을 사용하여 가져오기/내보내기가 예상보다 오래 걸릴 때 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다.
exl-id: d294b30d-b734-4bd6-bf1a-c116b789a63c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-31021: 제품 옵션이 많은 경우 가져오기 및 내보내기 속도가 느림

MDVA-31021 패치는 많은 제품 옵션을 사용하여 가져오기/내보내기가 예상보다 오래 걸릴 때 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.3.1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

에 10만 개 이상의 레코드가 있는 경우 `catalog_product_option` 표에서 가져오기/내보내기 기능 파일의 유효성 검사가 예상보다 오래 걸립니다. 가져오기/내보내기 전에 옵션 유효성 검사를 확인하기 위해 Adobe Commerce은 모든 기존 제품에 대한 제품 옵션을 로드합니다.

<u>전제 조건</u>:

Adobe Commerce 스토어에 사용자 지정 옵션이 있는 5000 제품이 있습니다. 각 제품에는 100,000개의 레코드가 있을 수 있도록 둘 이상의 선택 사항이 있는 최소 4개의 사용자 지정 옵션이 있어야 합니다. `catalog_product_option` 테이블.

<u>재현 단계</u>:

1. 의 경우 **가져오기** 예: Commerce 관리자의 SKU 중 하나를 사용하여 CSV 가져오기 파일을 만듭니다.
1. 4개의 사용자 지정 옵션을 CSV 가져오기 파일에 추가합니다.
1. Commerce 관리자에서 CSV 파일을 가져오려고 합니다.

<u>예상 결과</u>:

가져오기 또는 내보내기 기능은 예상대로 완료됩니다. 유효성 검사는 하나의 제품으로 완료하는 데 10초 미만이 소요됩니다.

<u>실제 결과</u>:

가져오기 또는 내보내기 기능이 예상보다 오래 걸립니다. 유효성 검사는 하나의 제품만으로 완료하는 데 10초 이상 걸립니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
