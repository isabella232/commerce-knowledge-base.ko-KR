---
title: 'ACSD-54418: 동적으로 가격이 책정된 번들의 하위 제품에 잘못 추가된 고정 할인 금액'
description: ACSD-54418 패치를 적용하여 고정 할인 금액이 동적으로 가격이 책정된 번들의 각 하위 제품에 잘못 적용되는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart
role: Admin, Developer
exl-id: f9a00a4b-0a57-4a61-8b7c-6385e0751991
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-54418: 동적으로 가격이 책정된 번들의 하위 제품에 잘못 추가된 고정 할인 금액.

ACSD-54418 패치는 고정 할인 금액이 동적으로 가격이 책정된 번들의 각 하위 제품에 잘못 적용되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.42가 설치되어 있습니다. 패치 ID는 ACSD-54418입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고정 할인 금액이 동적으로 가격이 책정된 번들의 각 하위 제품에 잘못 적용됩니다.

<u>재현 단계</u>:

1. 만들기 **[!UICONTROL bundle product]** 동적 가격 및 *2* 번들 옵션.
1. 만들기 **[!UICONTROL cart price rule]** 번들 제품에만 적용되는 특정 쿠폰 코드 사용 **[!UICONTROL SKU]** 그리고 고정 할인이 있습니다.
1. 번들 제품을 장바구니에 추가합니다.
1. 적용 **[!UICONTROL coupon code]**.
1. 장바구니에 적용되는 할인을 확인하십시오.

<u>예상 결과</u>:

전체 묶음 상품에 한 번만 할인이 적용됩니다.

<u>실제 결과</u>:

할인은 각 번들 하위 제품에 적용됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
