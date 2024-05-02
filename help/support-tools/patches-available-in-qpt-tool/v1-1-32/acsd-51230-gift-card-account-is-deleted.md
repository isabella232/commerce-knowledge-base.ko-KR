---
title: 'ACSD-51230: 기프트 카드 계정이 삭제됨'
description: ACSD-51230 패치를 적용하여 주문에서 단순 제품의 부분 환불이 처리될 때 기프트 카드 계정이 삭제되는 Adobe Commerce 문제를 해결합니다.
exl-id: 4322a175-3641-468a-8a0f-fcbad90c758f
feature: Customer Service, Gift, Marketing Tools
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-51230: 기프트 카드 계정이 삭제됨

ACSD-51230 패치는 주문에서 단순 제품의 일부 환불이 처리되는 경우 기프트 카드 계정이 삭제되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.32가 설치되어 있습니다. 패치 ID는 ACSD-51230입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문에서 간편상품 일부 환불 처리 시 기프트카드 계정이 삭제됩니다.

<u>재현 단계</u>:

1. 을(를) 사용하여 주문 만들기 *기프트 카드* 및 a *단순 제품* (예: *추가: SKU: GI000XX000XXX, SKU: PC046CP042076*) - (모든 결제 및 배송 방법이 작동합니다.)
1. 주문에 대한 송장을 발행합니다.
1. 다음으로 이동 **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. 기프트 카드에 대한 계정이 만들어집니다.
1. 이제 다음으로 이동 **[!UICONTROL Order]**, 및 만들기 **[!UICONTROL Credit Memo]**.
1. 에 대한 수량 변경 *기프트 카드* 을(를) 0으로 설정하고 을(를) 업데이트합니다. 이렇게 하면 다음에 대한 부분 환불이 생성됩니다. *단순 제품*.
1. 클릭 **[!UICONTROL Refund]**.
1. 이제 새로 고침 **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. 새로 만든 계정이 삭제됩니다.

<u>예상 결과</u>

기프트 카드 계좌는 기프트 카드에 대한 환불이 생성되지 않아 사용할 수 있습니다.

<u>실제 결과</u>

기프트 카드 계좌는 삭제되고 기프트 카드는 환불이 되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
