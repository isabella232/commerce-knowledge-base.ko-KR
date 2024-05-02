---
title: 'MDVA-39305: 활성화된 Google reCAPTCHA의 로그인 문제'
description: MDVA-39305 패치는 등록된 고객이 활성화된 Google reCAPTCHA로 로그인할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39305입니다. 이 문제는 Adobe Commerce 버전 2.4.4 및 2.4.7에서 수정됩니다.
exl-id: 1e8e7dc7-f8f1-4432-90f4-dc73d85f353a
feature: Console
role: Admin
source-git-commit: d48abbf3ecc19a78ee1d86a12d9c32cba17d53e5
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-39305: Google reCAPTCHA가 활성화된 경우 로그인 문제

MDVA-39305 패치는 등록된 고객이 활성화된 Google reCAPTCHA로 로그인할 수 없는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1이 설치되었습니다. 패치 ID는 MDVA-39305입니다. 이 문제는 Adobe Commerce 버전 2.4.4 및 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* 클라우드 인프라의 Adobe Commerce 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

등록된 고객은 활성화된 Google reCAPTCHA를 사용하여 로그인할 수 없습니다.

<u>재현 단계</u>:

1. 다음으로 이동 **저장** > **구성** > **보안** > **Google reCAPTCHA Storefront** 및 활성화 **Google recaptcha**.
1. 다음으로 이동 **프론트엔드**.
1. 열기 **개발자 도구 콘솔** 을 클릭합니다.

<u>예상 결과</u>:

콘솔에 CSP 경고가 없습니다.

<u>실제 결과</u>:

콘솔의 CSP 경고.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
