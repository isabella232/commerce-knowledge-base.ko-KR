---
title: '''MDVA-35910: ''고객으로 로그인''이 비활성화되면 양식 유효성 검사가 중단됨'''
description: MDVA-35910 패치는 **고객으로 로그인** 확장이 비활성화될 때 고객 계정 만들기 양식 유효성 검사가 중단되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-35910입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
exl-id: fa63d725-33f0-4422-bcd5-d62dfee01b65
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-35910: &quot;고객으로 로그인&quot;이 비활성화되면 양식 유효성 검사가 중단됨

MDVA-35910 패치는 다음과 같은 경우 고객 계정 만들기 양식 유효성 검사가 중단되는 문제를 해결합니다. **고객으로 로그인** 확장이 비활성화되었습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치되었습니다. 패치 ID는 MDVA-35910입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.1-2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 다음으로 이동 **스토어 > 구성 > 고객**. 사용 안 함 **고객으로 로그인** 관리에서.
1. 아래 **고객으로 로그인**, 설정됨 **확장 사용** = *아니요*.
1. 구성을 저장하고 캐시를 플러시합니다.
1. 상점으로 돌아가 **등록** (고객 계정 만들기).
1. 계정 양식을 작성하고 유효성 검사가 **이메일 확인** 이(가) 작동하는지 여부를 확인합니다.

<u>예상 결과</u>:

고객 계정 만들기 프로세스는 오류 없이 완료됩니다.

<u>실제 결과</u>:

고객 계정 만들기 프로세스가 완료되지 않고 Javascript 콘솔 오류가 대신 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
