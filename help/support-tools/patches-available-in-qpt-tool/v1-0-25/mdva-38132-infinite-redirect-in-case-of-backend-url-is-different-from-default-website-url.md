---
title: 'MDVA-38132: 백엔드 URL이 기본 웹 사이트 URL과 다른 경우 무한 리디렉션'
description: MDVA-38132 패치는 백엔드 URL이 기본 웹 사이트 URL과 다를 경우 무한 리디렉션 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38132입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 122145d7-0961-47f8-8ab6-a15d62996e49
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38132: 백엔드 URL이 기본 웹 사이트 URL과 다른 경우 무한 리디렉션

MDVA-38132 패치는 백엔드 URL이 기본 웹 사이트 URL과 다를 경우 무한 리디렉션 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25가 설치되어 있습니다. 패치 ID는 MDVA-38132입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**
클라우드 인프라의 Adobe Commerce 2.3.4-p2

**Adobe Commerce 버전과 호환:**
Adobe Commerce(모든 배포 방법) 2.3.3-2.4.2-p1
>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

백엔드 URL이 기본 웹 사이트 URL과 다른 경우 Commerce 관리 패널에는 무한 리디렉션이 있습니다.

<u>전제 조건</u>:

* 기본 URL은 백엔드와 상점 모두에 사용됩니다. 기본 보안 URL이 사용되지 않습니다.
* 웹 서버는 두 개의 다른 URL을 통해 Adobe Commerce에 액세스할 수 있도록 구성되어 있습니다. URL1은 Adobe Commerce 설치에 사용됩니다.

<u>재현 단계</u>:

1. 관리 패널 로 이동 > **스토어** > **구성** > **웹**.
1. 전역 구성에서 원래 기본 URL은 그대로 둡니다. URL1입니다.
1. 기본 웹 사이트 범위로 전환합니다.
1. 기본 URL을 다른 URL로 변경합니다(웹 서버를 올바르게 설정하려면 사전 조건 참조). URL2입니다.
1. 캐시를 지웁니다(필요한 경우).
1. 관리자 패널을 엽니다.

<u>예상 결과</u>:

관리자 패널이 성공적으로 열렸으며 탐색할 수 있습니다. 기본 웹 사이트의 저장소가 성공적으로 열렸고 탐색할 수 있습니다.

<u>실제 결과</u>:

무한 리디렉션이 발생합니다. Adobe Commerce은 URL1에서 URL2로 리디렉션하고 앞뒤로 계속 이동합니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT 도구에서 사용할 수 있는 다른 패치에 대한 자세한 내용은 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션.
