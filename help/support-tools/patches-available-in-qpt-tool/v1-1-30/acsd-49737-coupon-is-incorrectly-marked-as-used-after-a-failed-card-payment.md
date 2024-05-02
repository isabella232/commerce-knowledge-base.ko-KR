---
title: 'ACSD-49737: 쿠폰이 카드 결제 실패 후 사용된 것으로 잘못 표시됨'
description: ACSD-49737 패치를 적용하여 카드 결제가 실패한 후 쿠폰이 사용된 것으로 잘못 표시되는 Adobe Commerce 문제를 해결합니다.
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737: 쿠폰이 다음으로 잘못 표시됨 *사용됨* 카드 결제 실패 후

ACSD-49737 패치를 사용하면 쿠폰이 로 잘못 표시되는 문제가 해결됩니다. *사용됨* 카드 결제에 실패한 후. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되었습니다. 패치 ID는 ACSD-49737입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

쿠폰이 (으)로 잘못 표시됨 *사용됨* 카드 결제에 실패한 후.

<u>전제 조건</u>:

1. 구성 **[!UICONTROL Braintree sandbox payment]** 메서드를 사용합니다.
1. 다음을 확인합니다. [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) 소비자가 설정 및 실행 중입니다.

<u>재현 단계</u>:

1. 만들기 **[!UICONTROL Cart Price Rule]** (자동 생성된 쿠폰 코드 사용)
1. 고객으로 로그인.
1. 장바구니에 제품을 추가합니다.
1. 자동 생성된 쿠폰 코드를 적용합니다.
1. 결제가 실패한 주문을 시도해 보십시오.
1. 에서 쿠폰 사용 확인 **[!UICONTROL Cart Price Rule]** 다음 아래에 **[!UICONTROL Manage Coupon Codes]** 탭.

<u>예상 결과</u>:

쿠폰은 다음으로 플래그가 지정될 수 없습니다. *사용됨* 결제가 실패한 경우.

<u>실제 결과</u>:

* 쿠폰 코드에는 - 사용됨: *예*, 사용된 시간: *1*
* 쿠폰 코드는 한 번만 사용할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 패치 설치 후 추가 단계 필요

(이 섹션은 선택 사항입니다. 문제를 해결하기 위해 패치를 적용한 후 몇 가지 단계가 필요할 수 있습니다.) 

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
