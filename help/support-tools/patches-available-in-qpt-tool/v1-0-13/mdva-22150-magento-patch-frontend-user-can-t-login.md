---
title: "MDVA-22150 Adobe Commerce 패치: 프론트엔드 사용자가 로그인할 수 없음"
description: MDVA-22150 패치는 쿠폰을 사용하여 구매를 중단한 후 프론트엔드 사용자가 로그인할 수 없는 문제를 해결합니다. 이 문제는 프론트엔드 사용자가 구매를 완료하기 전에 비활성화된 제품에서 쿠폰 코드를 사용할 때 발생합니다. 그 결과 프론트엔드 사용자는 더 이상 로그인할 수 없으며 503 오류가 표시됩니다. 이 문제의 또 다른 효과는 관리자에서 고객의 장바구니를 관리하는 기능이 작동하지 않는다는 것입니다.
exl-id: 8aabe7b2-4b8a-4339-914e-7131006907b3
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# MDVA-22150 Adobe Commerce 패치: 프론트엔드 사용자가 로그인할 수 없음

MDVA-22150 패치는 쿠폰을 사용하여 구매를 중단한 후 프론트엔드 사용자가 로그인할 수 없는 문제를 해결합니다. 이 문제는 프론트엔드 사용자가 구매를 완료하기 전에 비활성화된 제품에서 쿠폰 코드를 사용할 때 발생합니다. 그 결과 프론트엔드 사용자는 더 이상 로그인할 수 없으며 503 오류가 표시됩니다. 이 문제의 또 다른 효과는 관리자에서 고객의 장바구니를 관리하는 기능이 작동하지 않는다는 것입니다.

이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13이 설치되었습니다. 이 문제는 Adobe Commerce 버전 2.3.4에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.** 클라우드 인프라의 Adobe Commerce 2.3.2

**Adobe Commerce 버전과 호환:** 클라우드 인프라의 Adobe Commerce 및 Adobe Commerce 2.3.1 - 2.3.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계:</u>

1. 관리자에 로그인하고 구성 가능한 제품을 만듭니다.
1. 다음으로 이동 **장바구니 규칙**&#x200B;할인 쿠폰이 포함된 쿠폰을 생성할 수 있습니다.
1. 프론트엔드에 고객 계정을 만듭니다.
1. 장바구니에 제품을 추가하고 체크아웃 프로세스를 수행한 다음 쿠폰을 입력합니다.
1. 쿠폰 입력 후 주문서를 제출하지 말고, 주문 중단 후 로그아웃합니다.
1. 관리자로 돌아가 구성 가능한 전체 제품을 비활성화합니다.

<u>예상 결과:</u>

제품이 상점 앞의 장바구니에 표시되지 않거나, 예상대로 제품이 비활성화되었다는 적절한 오류 메시지가 표시되지 않습니다.

<u>실제 결과:</u>

* 프론트엔드에 다시 로그인하려고 하면 무한 루프에 갇히게 됩니다(긴 시간 후에 예외 표시).
* 관리자의 고객 장바구니 관리 기능이 작동하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션.
