---
title: 'ACSD-55241: **Used** 및 **Times Used** 속성에 생성된 쿠폰에 대한 잘못된 값이 표시됨'
description: ACSD-55241 패치를 적용하여 **사용된 시간** 및 **사용된 시간** 속성에 생성된 쿠폰에 대한 잘못된 값이 표시되는 Adobe Commerce 문제를 해결합니다
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: 5d0b4743fe49d22c099102490f93dc4065ab4413
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241: **사용됨** 및 **사용된 시간** 생성된 쿠폰에 대해 잘못된 값이 속성에 표시됨

ACSD-55241 패치를 사용하면 다음과 같은 문제가 해결됩니다. **사용됨** 및 **사용된 시간** 속성은 생성된 쿠폰에 대해 잘못된 값을 표시합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.47이 설치되었습니다. 패치 ID는 ACSD-55241입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**사용됨** 및 **사용된 시간** 속성은 생성된 쿠폰에 대해 잘못된 값을 표시합니다.

<u>재현 단계</u>:

1. 만들기 **[!UICONTROL Cart Price Rules]** 출처: **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** 주문 중에 일치하는 조건을 추가합니다(예: 보다 큰 소계). *5$*)

* 할인을 적용합니다.
* 선택 **[!UICONTROL Auto Coupon]**.
* 에서 몇 가지 쿠폰 코드를 생성합니다. **쿠폰 코드 관리**.
* 캐시를 다시 인덱싱하고 정리합니다.

1. 만들기 **[!UICONTROL customer account]** 프론트엔드에 로그인합니다.
1. 개 이상의 제품을 추가합니다. *2* 장바구니에서 수량을 확인하고 쿠폰 하나를 적용합니다.
1. 클릭 **[!UICONTROL Check Out with Multiple Addresses]**.
1. 각 수량에 대해 별도의 주소를 선택하고 주문을 지정한 다음 체크아웃 프로세스를 완료합니다.
1. 관리자의 주문 합계를 확인하고 적용된 할인을 확인합니다.
1. 다른 쿠폰으로 다시 주문하세요.
1. 실행 `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` 쿠폰 코드 사용을 업데이트하는 명령입니다.

<u>예상 결과</u>:

올바른 개수를 **사용된 시간** 및 **사용됨** 열 **예** 값 **[!UICONTROL manage coupon]** 다음에서 **[!UICONTROL cart price rule]** 관리자.

<u>실제 결과</u>:

사용된 쿠폰 코드 개수가에서 업데이트되지 않음 **사용된 시간** 쿠폰 표의 열 및 **사용됨** 열은 다음을 표시합니다. *아니요* 여러 배송 주소를 사용하여 주문하는 경우 값.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
