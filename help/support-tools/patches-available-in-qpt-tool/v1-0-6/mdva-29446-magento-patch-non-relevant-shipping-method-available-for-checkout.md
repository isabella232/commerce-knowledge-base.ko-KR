---
title: 'MDVA-29446: 체크아웃에 사용할 수 있는 관련 없는 배송 방법'
description: MDVA-29446 패치는 해당되지 않는 배송 방법이 체크아웃 배송 방법 옵션에 표시되는 문제를 해결했습니다. 이 옵션을 선택하면 오류 메시지 "*해당 방법이 있는 캐리어가 null, 정액 요금을 찾을 수 없습니다*"가 표시됩니다. 표시됩니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치된 경우 사용할 수 있습니다. 이 문제는 이후 Adobe Commerce 버전에서 수정되도록 예약되었습니다.
exl-id: 74de5ec4-1f57-4d63-8fbc-614b23783ee3
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-29446: 체크아웃에 사용할 수 있는 관련 없는 배송 방법

MDVA-29446 패치는 해당되지 않는 배송 방법이 체크아웃 배송 방법 옵션에 표시되는 문제를 해결했습니다. 이 옵션을 선택하면 오류 메시지가 표시됩니다.*해당 메서드를 사용하는 통신사가 null, 정액 요금을 찾을 수 없음*.&quot; 표시됩니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치되었습니다. 이 문제는 이후 Adobe Commerce 버전에서 수정되도록 예약되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* 클라우드 인프라의 Adobe Commerce 2.3.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.3-2.4.0.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

적용할 수 없지만 체크아웃 운송 방법 옵션에 여전히 표시되는 운송 방법이 있으며 이 관련성이 없는 운송 방법을 선택할 수 있습니다.

<u>재현 단계</u>:

1. Clean 2.3-develop을 설치합니다.
1. 정액 요금 활성화 및 설정:

   * 해당 국가로 출하 = *특정 국가*
   * 특정 국가로 출하 = *남극 대륙*
   * 해당되지 않는 경우 메서드 표시 = *예*

1. 다른 모든 배송 방법을 비활성화합니다.
1. 프론트엔드로 이동하여 미국 주소로 고객을 만듭니다.
1. 항목을 선택하고 **장바구니에 추가**.
1. 장바구니를 클릭하고 **체크아웃 진행**.

<u>실제 결과</u>:

1. 다음에서 **배송** 페이지에 다음이 표시됩니다.

   * 정액 요금이 표시됩니다.
   * 정액제 요금은 0$입니다.
1. 사용자가 클릭한 후 **다음**, 사용자에게 다음 오류가 표시됩니다.

*&quot;해당 메서드를 사용하는 통신사를 찾을 수 없음: null, flatrate&quot;*

<u>예상 결과</u>:

* 배송 방법을 적용할 수 없는 경우 배송 방법의 가격이 표시되지 않습니다.
* 다음 **다음** 버튼이 활성화되지 않아야 합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
