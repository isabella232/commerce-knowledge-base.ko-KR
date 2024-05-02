---
title: 'ACSD-52824: 회사 고객에 대해 비활성화된 결제 방법 표시'
description: 'ACSD-52824 패치를 적용하여 Adobe Commerce 문제 해결 위치: [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] 회사 설정에서 결제 방법이 비활성화되어 있더라도 회사 고객에 대해 결제 방법이 나타납니다.'
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 03496fb1-d492-4f02-9cdc-466cb571a2eb
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52824: 회사 고객에 대해 비활성화된 결제 방법 표시

ACSD-52824 패치는 다음과 같은 문제를 해결합니다. [!DNL PayPal Express], [!DNL Google Pay], 및 [!DNL Apple Pay] 회사 설정에서 결제 방법이 비활성화되어 있더라도 회사 고객에 대해 결제 방법이 나타납니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45가 설치되어 있습니다. 패치 ID는 ACSD-52824입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

회사 고객에 대해 비활성화된 결제 방법이 표시됩니다.

<u>재현 단계</u>:

1. 구성 및 활성화 [!DNL PayPal Express Checkout]. 다음으로 이동 **[!UICONTROL Basic Settings]** > 선택 **[!DNL PayPal Express Checkout]** 옵션을 설정합니다. **[!UICONTROL Display on Shopping Cart]** 끝 *예*.
1. 구성 [!DNL Braintree] 및 활성화 [!DNL Apple Pay] 및 [!DNL Google Pay] 에서 [!DNL Braintree].
1. 다음으로 이동 **[!UICONTROL Customers]** > **[!UICONTROL Companies]** 새 회사를 만드십시오.
1. 클릭 **[!UICONTROL Advanced Settings]**, 다음 위치 찾기 **[!UICONTROL Applicable Payment Methods]** 및 선택 **[!UICONTROL Selected Payment Methods]**.
1. 아래 **[!UICONTROL Selected Payment Methods]**, 사용 가능하고 연결되어 있지 않은 결제 방법 선택 *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]*, 또는 *[!DNL Google Pay]*. 예를 들어 을 선택합니다. **[!UICONTROL Check/Money Order]**.
1. 적절한 결제 방법을 선택한 후 신규 고객을 생성하고 이전에 생성한 회사와 연결합니다.
1. 회사와 연결된 고객 계정으로 로그인하고 계속 진행하여 장바구니에 항목을 추가합니다.
1. 체크아웃 과정에서 미니 장바구니, 장바구니, 결제 단계에 유의하세요.

<u>예상 결과</u>:

결제 방법: 부터 [!DNL PayPal] 및 [!DNL Braintree] 미니 장바구니 및 장바구니에 표시되지 않습니다.

<u>실제 결과</u>:

결제 방법: 부터 [!DNL PayPal] 및 [!DNL Braintree] 미니 장바구니 및 장바구니에 계속 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
