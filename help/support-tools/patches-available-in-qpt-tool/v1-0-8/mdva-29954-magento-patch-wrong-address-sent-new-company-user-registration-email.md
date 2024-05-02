---
title: 'MDVA-29954: 새 회사 사용자 등록 이메일을 보낸 잘못된 주소'
description: MDVA-29954 패치는 "새 회사 등록 요청" 및 "회사에 연결되었습니다" 이메일이 잘못된 이메일 주소에서 전송되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 9b3d1b93-3fe6-40a0-a68a-3e3d789c6d66
feature: B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29954: 새 회사 사용자 등록 이메일을 보낸 잘못된 주소

MDVA-29954 패치는 &quot;새 회사 등록 요청&quot; 및 &quot;회사에 연결되었습니다&quot; 이메일이 잘못된 이메일 주소에서 전송되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8이 설치되었습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.3.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.3.5-p2, 2.4.0 및 2.4.1.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>전제 조건</u>:

B2B와 함께 Adobe Commerce 설치 **B2B 기능** 및 **회사** 활성화되었습니다.

<u>재현 단계</u>:

1. 을(를) 클릭합니다 **계정 만들기** 상점 첫 화면의 드롭다운에서 **새 회사 계정 만들기**.
1. 필수 필드를 입력한 다음 계정을 등록합니다.
1. 활성화 **회사** 백엔드에서(**고객** > **회사**).
1. 등록에 사용한 이메일 주소를 확인합니다.
1. 설정 **회사 관리자 암호** 이메일 지침을 따릅니다.
1. 를 사용하여 프론트엔드에 로그인합니다. **회사 관리자 암호**.
1. 새로 만들기 **회사 사용자** 위치: **내 계정** > **회사 사용자** > **새 사용자 추가**.
1. 다음으로 이동 **스토어** > **구성** > **일반 저장 이메일 주소** > **일반 연락처**, 및 확인 **보낸 사람 이메일**.
1. 을(를) 등록하는 데 사용한 이메일로 이동합니다 **새 사용자** 7단계.

<u>예상 결과</u>:

&quot;회사에 연결되었습니다&quot; 이메일이 와 동일한 값의 이메일 주소에서 전송됩니다. **보낸 사람 이메일** 8단계.

<u>실제 결과</u>:

&quot;회사에 연결되었습니다&quot; 이메일이 **회사 관리자** 이메일.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
