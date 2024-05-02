---
title: 숨김 [!DNL reCAPTCHA] 체크아웃 중에 실패하여 주문 배치가 방지됨
description: ACSD-54656 패치를 적용하여 표시되지 않는 Adobe Commerce 문제를 해결합니다. [!DNL reCAPTCHA] 이(가) 체크아웃 중에 제대로 작동하지 않아 주문 배치가 되지 않습니다.
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656: 보이지 않음 [!DNL reCAPTCHA] 이(가) 체크아웃 중에 제대로 작동하지 않아 주문 배치가 되지 않습니다.

ACSD-54656 패치를 사용하면 표시되지 않는 문제가 해결됩니다. [!DNL reCAPTCHA] 이(가) 체크아웃 중에 제대로 작동하지 않아 주문 배치가 되지 않습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46이 설치되었습니다. 패치 ID는 ACSD-54656입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

숨김 [!DNL reCAPTCHA] 이(가) 체크아웃 중에 제대로 작동하지 않아 주문 배치가 되지 않습니다.

<u>재현 단계</u>:

1. 모든 유형의 활성화 [!DNL reCAPTCHA] (이)에 있는 기프트 카드용 [!UICONTROL Checkout] 페이지를 가리키도록 업데이트하는 중입니다.
1. 장바구니에 제품 추가 및 **[!UICONTROL Checkout]** 페이지를 가리키도록 업데이트하는 중입니다.
1. 기프트 카드 양식을 확장하고 유효한 기프트 카드 쿠폰을 입력합니다.
1. 클릭 **[!UICONTROL See balance and apply]** 단추를 클릭합니다.

<u>예상 결과</u>:

기프트 카드가 정상적으로 적용되었습니다.

<u>실제 결과</u>:

오류 메시지가 표시됩니다. *[!DNL reCAPTCHA]유효성 검사에 실패했습니다. 다시 시도하십시오.*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
