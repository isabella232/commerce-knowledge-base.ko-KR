---
title: 'MDVA-34867: 예약된 업데이트에 대한 조건 필드 집합 값이 저장되지 않음'
description: MDVA-34867 패치는 카탈로그 가격 규칙을 편집할 때 새 일정 업데이트의 조건 값이 저장되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
exl-id: bf514ccc-bebd-4ed2-868f-28b02b1e253e
feature: Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-34867: 예약된 업데이트에 대한 조건 필드 집합 값이 저장되지 않음

MDVA-34867 패치는 카탈로그 가격 규칙을 편집할 때 새 일정 업데이트의 조건 값이 저장되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17이 설치되었습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.4.0-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

카탈로그 가격 규칙을 편집할 때 새 일정 업데이트의 조건 값이 저장되지 않습니다.

<u>재현 단계</u>:

1. 관리자에 로그인합니다.
1. 만들기 **카탈로그 규칙** 포함 **조건** = &quot;*범주가 1임*&quot;.
1. 시작 날짜가 미래인 업데이트 예약(예: 내일) 및 설정 **조건** = &quot;*범주 2, 3*&quot;및 업데이트를 저장합니다.
1. 클릭 **보기/편집** 위에서 생성한 업데이트에 대해 조건 필드를 선택합니다.

<u>예상 결과</u>:

다음 **카탈로그 규칙**  **조건** = &quot;*범주 2, 3*&#x200B;예상대로 &quot;.

<u>실제 결과</u>:

다음 **카탈로그 규칙**  **조건** = &quot;*범주가 1임*&quot;: 업데이트가 저장되지 않았습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션.
