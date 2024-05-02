---
title: 'ACSD-43887: 체크아웃 결제 페이지에 잘못된 세부 정보가 표시됨'
description: ACSD-43887 패치는 회사의 구매 발주가 활성화되면 체크아웃 결제 페이지에 잘못된 세부 정보가 표시되는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-43887입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
exl-id: 07b17f96-5236-43a7-aeaf-6bfe36c551cf
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# ACSD-43887: 체크아웃 결제 페이지에 잘못된 세부 정보가 표시됨

ACSD-43887 패치는 회사의 구매 발주가 활성화되면 체크아웃 결제 페이지에 잘못된 세부 정보가 표시되는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치되었습니다. 패치 ID는 ACSD-43887입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

회사에 대한 구매 발주가 활성화되면 잘못된 세부 정보가 체크아웃 결제 페이지에 표시됩니다.

<u>전제 조건</u>:

1. B2B 모듈이 설치되어 있습니다.
1. 회사 활성화가 다음으로 설정됨 _예_. 다음으로 이동 **스토어** > **구성** > **일반** > **B2B 기능** > **회사 활성화** > **예**.
1. 구매 주문 활성화가 다음으로 설정됨 _예_. 다음으로 이동 **주문 승인 구성** > **구매 주문 활성화** > **예**.
1. PayPal Express는 결제 방법으로 구성됩니다.

<u>재현 단계</u>:

1. 가상 제품을 만듭니다.
1. 프론트엔드에서 회사 계정을 회사 관리자에게 등록합니다.
1. 백엔드에서 회사 계정을 승인하고 설정합니다. **구매 주문 활성화** 다음으로: _예_ 회사를 승인하는 동안.
1. 프론트엔드로 이동한 다음 2단계에서 만든 회사 관리자 계정을 사용하여 로그인합니다.
1. 회사에 대한 &quot;기본 사용자&quot;를 만듭니다. 다음으로 이동 **회사 사용자** > **새 사용자 추가**.
1. 회사에 대한 &quot;승인 규칙&quot;을 만듭니다. 다음으로 이동 **승인 규칙** > **새 규칙 추가**.

   * 규칙 유형: 주문 합계
   * 주문 합계: $1 이상입니다.
   * 승인 필요: 회사 관리자

1. 로그아웃한 후 &quot;기본 사용자&quot; 계정을 사용하여 로그인합니다.
1. 1단계에서 만든 가상 제품을 장바구니에 추가하고 체크아웃을 진행합니다.
1. 결제 방법으로 PayPal Express를 선택하고 을(를) 클릭합니다. **구매 주문**.
1. 회사 관리자 계정을 사용하여 로그아웃한 후 로그인합니다.
1. 다음으로 이동 **내 구매 주문** 및 출처 **회사 구매 주문**, 클릭 **보기** 9단계에서 생성된 주문의 경우.
1. 구매 주문을 승인합니다. 구매 발주 상태는 &quot;승인됨: 지급 대기 중&quot;이어야 합니다.
1. 회사 &quot;기본 사용자&quot; 계정을 사용하여 로그아웃하고 로그인합니다.
1. 다음으로 이동 **내 구매 주문** > **보기** > **주문**.
1. 다음 확인: **주문 요약**.

<u>예상 결과</u>:

주문 요약에는 0이 아닌 올바른 값이 표시됩니다.

<u>실제 결과</u>:

주문 요약 합계 값은 0입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
