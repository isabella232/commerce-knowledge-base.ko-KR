---
title: 'MDVA-35254: 체크아웃 CAPTCHA가 제대로 작동하지 않음'
description: MDVA-35254 패치는 타사 지불에 대한 체크아웃 시도 실패 횟수가 지난 후 CAPTCHA 필드가 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-35254입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
exl-id: 226c672b-3740-4a87-9ea1-66892acb9fe2
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-35254: 체크아웃 CAPTCHA가 제대로 작동하지 않음

MDVA-35254 패치는 타사 지불에 대한 체크아웃 시도 실패 횟수가 지난 후 CAPTCHA 필드가 표시되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치되었습니다. 패치 ID는 MDVA-35254입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.1-2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

CAPTCHA 구성:

1. 타사 결제 공급자를 설치하고 구성합니다(예: Braintree).
1. 다음으로 이동 **스토어 > 구성 > 고객 > 고객 구성 > CAPTCHA > Forms**.
1. 선택 **체크아웃/주문 중**.
1. 유지 **로그인 시도 실패 횟수** 기본값으로(기본값 = *3*).
1. 고객으로 로그인.
1. 장바구니에 제품을 추가합니다.
1. 체크아웃의 결제 섹션으로 이동합니다.
1. 선택 **신용 카드** 결제 방법(예: Braintree)
1. 세 번 성공하지 못한 결제 시도.

<u>예상 결과</u>:

실패한 시도 횟수에 도달하면 CAPTCHA 필드가 표시됩니다.

<u>실제 결과</u>:

CAPTCHA 필드는 표시되지 않고 오류 메시지만 표시됩니다. *CAPTCHA 코드를 입력하고 다시 시도하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
