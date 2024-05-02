---
title: 'ACSD-54680: 여러 개의 할당된 소스가 있는 제품에 대한 B2B 견적을 처리할 수 없음'
description: ACSD-54680 패치를 적용하여 여러 개의 할당된 소스가 있는 제품에 대한 B2B 견적을 처리할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: B2B
role: Admin, Developer
exl-id: 4d05714c-d32d-46f3-b857-81704c9e96cd
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-54680: 여러 개의 할당된 소스가 있는 제품에 대한 B2B 견적을 처리할 수 없습니다.

ACSD-54680 패치는 여러 개의 할당된 소스가 있는 제품에 대한 B2B 견적을 처리할 수 없는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.40이 설치되었습니다. 패치 ID는 ACSD-54680입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

여러 개의 할당된 소스가 있는 제품에 대한 B2B 견적을 처리할 수 없습니다.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** 새 소스를 두 개 만듭니다. **소스 1** 및 **소스 2**.
1. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** 새 Stock 만들기: **재고 A**&#x200B;을(를) 기본 웹 사이트에 할당하고 을(를) 할당합니다 **소스 1** 및 **소스 2** 할 수 있습니다.
1. 간단한 제품 만들기, 할당 **소스 1** 및 **소스 2**, 및 설정된 수량 = *2* 각 소스에 대해 (제품의 판매 가능 수량은 다음과 같아야 합니다. *4* 따라서).
1. 회사 계정을 만듭니다.
1. 로 이동 **[!UICONTROL Storefront]** 회사 계정에 로그인합니다.
1. 수량 = 인 단순 제품을 장바구니에 추가합니다. *4*.
1. 를 엽니다. *[!UICONTROL Shopping cart]* 및 클릭 **[!UICONTROL Request a quote]** 단추를 클릭합니다.
1. 댓글 및 견적 이름을 추가하고 **[!UICONTROL Send a Request]** 단추를 클릭합니다.
1. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. 최근에 제출된 견적을 엽니다.

<u>예상 결과</u>:

견적된 품목에는 주문한 제품이 포함되어 있습니다.

<u>실제 결과</u>:

견적이 지정된 항목 페이지 섹션이 비어 있어 견적을 처리할 수 없습니다.
`var/log/system.log` 다음 포함

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
