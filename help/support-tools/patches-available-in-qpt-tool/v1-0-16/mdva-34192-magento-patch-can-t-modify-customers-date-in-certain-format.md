---
title: "MDVA-34192 패치: 특정 형식으로 고객 날짜를 수정할 수 없음"
description: MDVA-34192 패치는 dd/mm/yyyy 형식을 사용하여 고객 생년월일을 수정/지정할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-34192 패치: 특정 형식으로 고객 날짜를 수정할 수 없음

MDVA-34192 패치는 dd/mm/yyyy 형식을 사용하여 고객 생년월일을 수정/지정할 수 없는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16이 설치되었습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.** 클라우드 인프라의 Adobe Commerce 2.3.5-p1

**Adobe Commerce 버전과 호환:** 2.3.4-2.3.6

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이 패치는 몇 가지 문제를 해결합니다. 다음은 이 중 하나에 대한 설명 및 재현 단계입니다.

사용자 지정 날짜 속성을 사용하여 필터링하고 관리자 사용자 로케일이 en\_GB인 경우 제품 그리드 필터가 제대로 작동하지 않습니다.

<u>재현 단계:</u>:

1. 다음의 관리 사용자 만들기 **인터페이스 로케일** 이(가) (으)로 설정됨 *영어(영국)*.
1. 다음 구성으로 날짜 속성을 만듭니다.
   * **저장소 소유자에 대한 카탈로그 입력 유형**: *날짜*
   * **필터 옵션에서 사용**: *예*
   * **열에 추가 옵션**: *예*
1. 속성을 속성 세트에 지정합니다.
1. 제품 편집 페이지로 이동하여 날짜 선택기를 사용하여 새 속성의 날짜를 선택하고 저장합니다.
1. 새 날짜 속성을 사용하여 제품 그리드를 필터링하십시오.

<u>예상 결과:</u>:

제품 필터는 관리자 사용자 로케일이 en\_GB인 경우 사용자 지정 날짜 속성에 대해 올바르게 작동합니다.

<u>실제 결과:</u>:

관리자 사용자 로케일이 en\_GB인 경우 사용자 지정 날짜 속성에 대해 제품 필터가 제대로 작동하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT 도구에서 사용할 수 있는 다른 패치에 대한 자세한 내용은 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션.
