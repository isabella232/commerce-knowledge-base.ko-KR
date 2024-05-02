---
title: 'ACSD-49849: 고객 이메일이 PayPal 이메일로 대체됨'
description: ACSD-49849 패치를 적용하여 GraphQL을 통해 PayPal Express로 주문할 때 고객 이메일이 PayPal 이메일로 대체되는 Adobe Commerce 문제를 해결합니다.
exl-id: 826ea90a-ac10-43e8-aa88-bd69b152ded8
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-49849: 고객 이메일이 (으)로 대체됨 [!DNL PayPal] 이메일

ACSD-49849 패치는 고객 이메일이 로 대체되는 문제를 해결합니다. [!DNL PayPal's] (으)로 주문 시 이메일 보내기 [!DNL PayPal Express] GraphQL을 통해 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29가 설치되었습니다. 패치 ID는 ACSD-49849입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객 이메일이 (으)로 대체됨 [!DNL PayPal's] (으)로 주문 시 이메일 보내기 [!DNL PayPal Express] GraphQL을 통해

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. 활성화 및 구성 [!DNL PayPal Express] 및 설정 **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. 다음으로 이동 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;간단한 제품을 만들 수 있습니다.
1. GraphQL을 사용하여 게스트 체크아웃을 완료합니다. 자세한 내용은 [GraphQL 체크아웃 튜토리얼](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) Adobe Commerce 개발자 설명서에서 확인할 수 있습니다.
1. 사용 [!DNL PayPal Express] 를 결제 방법으로 사용하십시오.
1. 다음 단계에서 사용한 이메일을 확인합니다. [장바구니에 대한 이메일 설정](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) Adobe Commerce 개발자 설명서에서 확인할 수 있습니다.
1. 주문이 처리되면 Adobe Commerce 관리자로 이동하여 작성된 주문에서 이메일을 확인합니다.

<u>예상 결과</u>:

이메일은 체크아웃 중에 설정된 것과 동일합니다.

<u>실제 결과</u>:

체크아웃 중에 설정된 전자 메일은 의 전자 메일 세트에 의해 재정의됩니다 [!DNL PayPal] 계정입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
