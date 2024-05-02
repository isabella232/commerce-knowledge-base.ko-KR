---
title: 'ACSD-47232: 쿠폰이 적용되지 않는 경우 [!UICONTROL Same as Billing Address] 선택함'
description: 다음과 같은 경우 쿠폰이 적용되지 않는 Adobe Commerce 문제를 해결하려면 ACSD-47232 패치를 적용합니다. [!UICONTROL Same as Billing Address] 이(가) 선택되었습니다.
exl-id: 29b95a0b-8792-4830-a1e5-ce977f8453ec
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232: 쿠폰이 적용되지 않는 경우 [!UICONTROL Same as Billing Address] 선택함

ACSD-47232 패치는 다음과 같은 경우 쿠폰이 적용되지 않는 문제를 해결합니다 **[!UICONTROL Same as Billing Address]** 이(가) 선택되었습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23이 설치되었습니다. 패치 ID는 ACSD-47232입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

쿠폰은 다음과 같은 경우 적용되지 않습니다. **[!UICONTROL Same as Billing Address]** 이(가) 선택되었습니다.

<u>재현 단계</u>:

1. Adobe Commerce을 설치합니다.
1. 가중치 = 인 간단한 제품 만들기 *8*.
1. 기본 청구 및 배송 주소로 새 고객을 만듭니다.
1. 쿠폰으로 장바구니 가격 규칙을 만듭니다.
   * 위치 **[!UICONTROL Conditions]** 섹션, 추가 *총 중량이 5보다 크거나 같음*
1. 에서 새 주문을 만들어 보십시오. [!UICONTROL Commerce] 관리자.
   * 방금 만든 고객 사용
   * 제품 추가
   * 쿠폰을 적용해 보세요

<u>예상 결과</u>:

쿠폰이 적용됩니다.

<u>실제 결과</u>:

다음과 유사한 오류가 발생합니다. *123 쿠폰 코드가 유효하지 않습니다. 코드를 확인하고 다시 시도하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
