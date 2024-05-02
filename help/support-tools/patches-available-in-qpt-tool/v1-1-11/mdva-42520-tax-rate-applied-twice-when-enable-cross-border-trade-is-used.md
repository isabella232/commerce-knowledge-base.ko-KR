---
title: 'MDVA-42520: "국경 간 거래 활성화"를 사용할 때 세율이 두 번 적용됨'
description: MDVA-42520 패치는 **국가 간 거래 활성화**를 사용할 때 세율이 두 번 적용되는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42520입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: c1ca44eb-fe92-4f28-807a-3a4563433386
feature: Catalog Management, Orders, Taxes
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-42520: &quot;국경 간 거래 활성화&quot;를 사용할 때 세율이 두 번 적용됨

MDVA-42520 패치는 다음과 같은 경우 세율이 두 번 적용되는 문제를 해결합니다. **국경 간 무역 사용** 를 사용합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11이 설치되었습니다. 패치 ID는 MDVA-42520입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

세율은 다음과 같은 경우에 두 번 적용됩니다. **국경 간 무역 사용** 를 사용합니다.

<u>재현 단계</u>:

1. 사용 **회사**, **공유된 카탈로그**, 및 **견적**
1. 스크린샷에 따라 세금을 구성합니다. 을(를) 활성화해야 합니다. **국경 간 무역**.

   ![세금 설정](/help/support-tools/patches-available-in-qpt-tool/assets/tax_settings_1.png){width="700"}

1. 독일에 대한 세율(10%)을 생성합니다.
1. 세율을 적용할 세금 규칙을 생성합니다.
1. 회사 및 사용자 지정 공유 카탈로그를 만듭니다.
1. 가격이 100인 제품을 만들고 가격 할인 20%의 사용자 지정 공유 카탈로그에 포함하십시오.
1. 독일 주소로 고객을 만들고 회사에 할당
1. 고객인 카드에 10개의 제품을 추가합니다.
1. 장바구니로 이동하여 견적을 요청합니다.
1. 백엔드에서 이 견적을 열고 10% 할인을 더 추가해 보십시오.

<u>예상 결과</u>:

견적 소계(세금 포함) 및 견적 총계(세금 포함) = $720

<u>실제 결과</u>:

견적 소계(세금 포함) 및 견적 총계(세금 포함) = $649.50.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
