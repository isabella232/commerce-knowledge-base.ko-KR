---
title: "MDVA-43731: '일치할 최소 용어'에 값을 추가하면 검색 동의어가 작동하지 않음"
description: MDVA-43731 패치는 "일치하는 최소 용어"에 값이 추가되면 검색 동의어 작동이 중지되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43731입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: b795989c-d10b-443e-aebe-f3859930396a
feature: Cache, Marketing Tools, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-43731: &#39;일치할 최소 용어&#39;에 값을 추가하면 검색 동의어가 작동하지 않습니다.

MDVA-43731 패치는 &quot;일치하는 최소 용어&quot;에 값이 추가되면 검색 동의어 작동이 중지되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치되어 있습니다. 패치 ID는 MDVA-43731입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

&quot;일치시킬 최소 용어&quot;에 값이 추가되면 검색 동의어 작동이 중지됩니다.

<u>재현 단계</u>:

1. 샘플 데이터를 사용하여 Adobe Commerce을 설치합니다.
1. Elasticsearch7을 검색 엔진으로 구성합니다.
1. &quot;Jacket&quot;이라는 단어를 검색합니다. 제품 목록이 표시됩니다.
1. 매개 변수 추가 [4&lt;60%] 위치: **구성** > **카탈로그** > **카탈로그 검색** > **일치시킬 최소 용어**.
1. 구성 캐시를 지우고 다시 인덱싱합니다.
1. 다시 &quot;재킷&quot;이라는 단어를 검색하고 제품 목록이 표시됩니다.
1. 다음으로 이동 **마케팅** > **SEO 및 검색** > **동의어 검색**.
1. jacket, bagtecs, express plus 와 같은 동의어를 추가하여 검색 동의어를 생성합니다.
1. 색인 재지정
1. 동의어를 사용하여 제품 검색을 수행합니다. 예, 재킷.

<u>예상 결과</u>:

검색 결과에서 이전과 동일한 제품 목록을 가져옵니다.

<u>실제 결과</u>:

검색 결과에 제품이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
