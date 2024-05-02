---
title: 'ACSD-44591: CAPTCHA 확인 없이 주문할 때 오류 발생'
description: ACSD-44591 패치는 CAPTCHA 확인 없이 주문을 하려고 할 때 사용자가 오류가 발생하는 문제를 해결합니다.
exl-id: 5459aa14-dcba-474d-aafa-e4cc73daafbc
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-44591: CAPTCHA 확인 없이 주문할 때 오류 발생

ACSD-44591 패치는 CAPTCHA 확인 없이 주문을 하려고 할 때 사용자가 오류가 발생하는 문제를 해결합니다.
이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치되었습니다. 패치 ID는 ACSD-44591입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 CAPTCHA 확인 없이 주문하려고 할 때 오류가 발생합니다.

<u>재현 단계</u>:

1. Google ReCaptcha v2(로봇이 아님)를 구성합니다.
1. 체크아웃을 위해 ReCaptcha를 활성화합니다.
1. ReCaptcha를 클릭하지 않고 주문해 보십시오.
1. 누락된 ReCaptcha에 대한 오류 메시지가 표시되면(*ReCaptcha 유효성 검사에 실패했습니다. 다시 시도하십시오.*), 클릭 **ReCaptcha** 그런 다음 주문을 시도해 보십시오.

<u>예상 결과</u>:

주문은 잘못된 ReCaptcha와 함께 제공되지 않습니다.

<u>실제 결과</u>:

다음과 같은 오류가 발생합니다.

* *ReCaptcha 유효성 검사에 실패했습니다. 다시 시도하십시오.*
* *ID = 1인 해당 장바구니 없음*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
