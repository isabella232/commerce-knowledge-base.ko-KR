---
title: 'MDVA-31307: 특정 범주의 메모리가 부족합니다.'
description: MDVA-31307 패치는 'Magento\_Csp/모델/블록 캐시'가 많은 메모리를 사용하고 엄청난 양의 캐시된 문자열을 생성하여 스크립트와 스타일이 동적으로 많이 화이트리스트에 추가되는 특정 페이지에 문제를 발생시키는 문제를 해결합니다. 제공된 패치는 이 프로세스를 최적화합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-31307입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307: 특정 범주에 메모리가 부족합니다.

MDVA-31307 패치는 다음과 같은 문제를 해결합니다. `Magento\_Csp/Model/BlockCache` 많은 메모리를 소비하고 캐시된 엄청난 문자열을 생성합니다. 이로 인해 스크립트와 스타일이 동적으로 많이 화이트리스트에 추가되는 특정 페이지에 문제가 발생합니다. 제공된 패치는 이 프로세스를 최적화합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치되었습니다. 패치 ID는 MDVA-31307입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.** 클라우드 인프라의 Adobe Commerce 2.4.0

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이 있는 문제를 수정합니다. *메모리 부족* 캐시된 블록에 대한 동적 CSP 허용 목록 문제로 인해 특정 범주에 오류가 발생합니다.

<u>재현 단계:</u>

1. 작은 프로필 고정장치 생성(`bin/magento setup:performance:generate-fixtures`).
1. 다른 탭에서 모든 범주 페이지를 엽니다.

<u>실제 결과:</u>

*[날짜 및 시간] PHP 치명적인 오류: 행 0에 있는 알 수 없음에 1073741824바이트의 허용된 메모리 크기(90112바이트를 할당하려고 시도함)
[날짜 및 시간] PHP 치명적인 오류: /app/에서 1073741824바이트의 메모리 크기를 허용했습니다(33554440바이트를 할당하려고 시도했습니다).`<project-id>`31행의 /vendor/magento/module-csp/Model/Collector/DynamicCollector.php*

<u>예상 결과:</u>

모든 페이지가 올바르게 열렸습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션.
