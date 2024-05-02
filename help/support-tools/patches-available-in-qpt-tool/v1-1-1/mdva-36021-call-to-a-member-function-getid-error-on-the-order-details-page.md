---
title: 'MDVA-36021: 사용자가 주문 세부 사항을 열 때 오류 메시지가 표시됨'
description: MDVA-36021 패치는 주문 세부 사항을 열려고 할 때 사용자가 멤버 함수 getId()* 오류 메시지에 *호출을 가져오는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-36021입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 73b1f3c6-5dc4-48e4-8f3f-681be84f7638
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-36021: 주문 세부 사항을 열 때 사용자에게 오류 메시지가 표시됨

MDVA-36021 패치는 사용자가 다음과 같은 문제를 해결합니다. *멤버 함수 getId() 호출* 주문 세부 사항을 열려고 할 때 오류 메시지가 표시됩니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1이 설치되었습니다. 패치 ID는 MDVA-36021입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* 클라우드 인프라의 Adobe Commerce 2.4.1, 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 주문 세부 사항을 열려고 하면 관리자의 주문 세부 사항 페이지에 다음 오류 메시지가 표시됩니다. *report.CRITICAL: 오류: /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62의 배열에서 멤버 함수 getId()를 호출합니다.*.

<u>전제 조건</u>:

동 제도는 세율과 세율의 체계를 갖추어야 한다.

<u>재현 단계</u>:

1. Commerce 관리자에 로그인합니다.
1. 다음으로 이동 **판매** > **주문 수** > **주문 열기**.

<u>예상 결과</u>:

주문이 오류 없이 열려 있습니다.

<u>실제 결과</u>:

다음과 유사한 오류 메시지가 표시됩니다. *report.CRITICAL: 오류: /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62의 배열에서 멤버 함수 getId()를 호출합니다.*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
