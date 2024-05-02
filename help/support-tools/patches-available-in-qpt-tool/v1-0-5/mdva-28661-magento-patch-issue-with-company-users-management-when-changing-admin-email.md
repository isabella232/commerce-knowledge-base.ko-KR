---
title: 'MDVA-28661: 관리자 이메일을 변경할 때 회사 사용자 관리에 문제가 발생'
description: MDVA-28861 패치는 사용자가 관리 이메일을 변경할 때 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-28861입니다.
exl-id: 2d6691e5-baaf-4cef-ae7e-2b6ccc7f2cd3
feature: Admin Workspace, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28661: 관리자 이메일을 변경할 때 회사 사용자 관리에 문제가 발생합니다.

MDVA-28861 패치는 사용자가 관리 이메일을 변경할 때 오류가 발생하는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5가 설치되어 있습니다. 패치 ID는 MDVA-28861입니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

B2B 확장이 있는 Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.0 - 2.4.1(2.3.5-p1 포함)

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

변경 후 **회사 관리자** 이메일 주소, 오류가 반환되고 **회사 사용자** 목록이 표시되지 않습니다.

<u>재현 단계</u>:

1. 회사 기능 활성화(다음에서 자세히 알아보기) [B2B 설치: Commerce 관리자에서 B2B 기능을 활성화합니다](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin) 개발자 설명서에서 관리자 및 사용자 2명(모두 이메일 주소 포함) 두 명의 사용자로 새 회사를 만듭니다.
1. 로 이동 **Commerce 관리자** > **고객** > **회사** 회사 계정을 엽니다.
1. 열기 **회사 관리자** 탭을 클릭하고 관리자를 첫 번째 사용자로 변경합니다. 여기에는 **회사 관리자** 첫 번째 사용자의 전자 메일로 보냅니다.
1. Adobe Commerce 프론트엔드로 이동하여 첫 번째 사용자로 로그인합니다.
1. 로 이동 **회사 사용자** 섹션.

<u>예상 결과</u>:

다음 **회사 사용자** 목록이 예상대로 표시되어야 합니다.

<u>실제 결과</u>:

다음 **회사 사용자** 목록이 표시되지 않고 다음과 유사한 오류가 표시됩니다.

```bash
No such entity with id = 2
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.

B2B 회사 기능에 대한 자세한 내용은 개발자 설명서에서 다음 문서를 참조하십시오.

* [B2B 개발자 안내서](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [회사 역할 관리](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Adobe Commerce Enterprise B2B 확장 구성 경로 참조](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
