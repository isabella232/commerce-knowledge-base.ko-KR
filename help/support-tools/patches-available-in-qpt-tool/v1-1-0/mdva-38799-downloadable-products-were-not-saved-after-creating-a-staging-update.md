---
title: 'MDVA-38799: 스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않음'
description: MDVA-38799 패치는 스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38799입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
exl-id: 306f9ef3-ca3a-41b9-a5d3-42aa4ef59953
feature: Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-38799: 스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않음

MDVA-38799 패치는 스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0이 설치되었습니다. 패치 ID는 MDVA-38799입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* 클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0-2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않습니다. 사용자에게 다음과 같은 오류 메시지가 표시됩니다. *다운로드 가능한 샘플은 제품과 관련이 없습니다. 링크를 확인하고 다시 시도하십시오*.

<u>재현 단계</u>:

1. 다음으로 이동 **카탈로그** > **제품**.
1. 제품 추가 옆에 있는 드롭다운을 클릭하고 다운로드 가능한 제품을 선택합니다.
   * 제품의 이름, SKU, 가격 및 수량을 입력합니다.
1. 다운로드 가능한 정보 페이지로 스크롤합니다.
1. 샘플에서 **링크 추가**.
   * 제목, 파일 업로드 를 채웁니다(파일 유형은 중요하지 않음).
1. 클릭 **저장**. 다음 메시지가 표시됩니다. *제품을 저장했습니다.*.
1. 클릭 **새 업데이트 예약** 을 클릭합니다.
   * 업데이트 이름과 법적 시작 날짜 및 종료 날짜를 입력합니다.
1. 클릭 **저장** 스테이징 업데이트 시.
1. 클릭 **저장** 제품에 대해 설명합니다.

<u>예상 결과</u>:

제품이 오류 없이 저장됩니다.

<u>실제 결과</u>:

다음과 같은 오류 메시지가 표시됩니다. *다운로드 가능한 샘플은 제품과 관련이 없습니다. 링크를 확인하고 다시 시도하십시오*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
