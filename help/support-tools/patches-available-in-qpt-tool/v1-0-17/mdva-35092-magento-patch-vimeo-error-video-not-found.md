---
title: '"MDVA-35092: Vimeo 오류: "비디오를 찾을 수 없음"""'
description: '"MDVA-35092 패치는 다음 오류가 표시되는 문제를 해결합니다. *"비디오를 찾을 수 없음"*. 이 오류 메시지는 Adobe Commerce 제품 관리자의 기본 비디오 추가 인터페이스를 사용하여 Vimeo 비디오를 입력하는 경우 표시됩니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17이 설치된 경우 사용할 수 있습니다. Adobe Commerce 2.4.3에서 문제가 해결되었습니다.'''
exl-id: bc0952d9-1ea4-417c-926c-96875984d82c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# MDVA-35092: Vimeo 오류: &quot;비디오를 찾을 수 없음&quot;

MDVA-35092 패치는 오류가 표시되는 문제를 해결합니다. *&quot;비디오를 찾을 수 없음&quot;*. 이 오류 메시지는 Adobe Commerce 제품 관리자의 기본 비디오 추가 인터페이스를 사용하여 Vimeo 비디오를 입력하는 경우 표시됩니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17이 설치되었습니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.5 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Vimeo 단순 API가 예상대로 작동하지 않습니다.

<u>재현 단계</u>:

1. 관리자에 로그인합니다.
1. 기존 제품을 편집하려면 **카탈로그** > **제품** > **편집**&#x200B;또는 새 제품을 만들려면 **카탈로그** > **제품** > **편집** > **제품 추가**.
1. 다음을 클릭합니다. **이미지 및 비디오** 제품 페이지의 탭입니다.
1. 클릭 **비디오 추가** Vimeo 비디오의 URL을 추가합니다. 클릭 **저장**.

<u>예상 결과</u>:

새 비디오를 찾아 저장합니다.

<u>실제 결과</u>:

오류: *&quot;비디오를 찾을 수 없음&quot;* 이 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션.
