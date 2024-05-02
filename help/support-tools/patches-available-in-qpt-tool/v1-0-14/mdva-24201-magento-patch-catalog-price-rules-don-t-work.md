---
title: "MDVA-24201: 카탈로그 가격 규칙이 작동하지 않음"
description: MDVA-24201 패치는 데이터베이스의 활성 카탈로그 가격 규칙이 프런트 엔드에 적용되지 않는 문제를 해결합니다.
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201: 카탈로그 가격 규칙이 작동하지 않음

MDVA-24201 패치는 데이터베이스의 활성 카탈로그 가격 규칙이 프런트 엔드에 적용되지 않는 문제를 해결합니다.

이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14가 설치되어 있습니다. 이 문제는 Adobe Commerce 버전 2.3.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.** 클라우드 인프라의 Adobe Commerce 2.3.3

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>전제 조건</u>:

샘플 데이터를 사용하여 새 Magento 인스턴스를 설치합니다.

<u>재현 단계</u>:

1. 에 로그인 **관리 패널** > **마케팅** > **카탈로그 가격 규칙** > **새 규칙 추가**&#x200B;을 설정하고 다음 설정을 수행합니다.
   1. 설정 **규칙 이름**.
   1. 설정 **활성** = *아니.*
   1. 조건 설정: **범주** = *4*. (예: 가방)
   1. 작업 설정:
      1. 설정 **다음으로 적용**   **원본 비율**.
      1. 설정 **할인 금액** = *10*.
      1. 저장한 다음 편집을 계속합니다.
   1. 클릭 **새 업데이트 예약**:
      * 설정 **규칙 이름**.
      * 설정 **활성** = *예*.
      * 저장.
1. 백엔드로 이동하여 다음을 실행합니다.

   `php    bin/magento cron:run`

<u>예상 결과</u>:

범주 4 &#39;가방&#39;의 상품가격은 예정대로 카탈로그 가격 규정에 의해 책정되었으므로 원래 가격의 10% 인하되어야 한다.

<u>실제 결과</u>:

카탈로그 가격 규칙이 활성 상태에서도 가격 변경이 발생하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션.
