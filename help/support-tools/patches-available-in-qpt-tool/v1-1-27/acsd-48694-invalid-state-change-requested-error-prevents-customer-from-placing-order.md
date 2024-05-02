---
title: 'ACSD-48694: 잘못된 상태 변경 요청 오류로 인해 고객이 주문을 할 수 없음'
description: ACSD-48694 패치를 적용하여 *잘못된 상태 변경 요청* 오류로 인해 고객이 주문을 할 수 없는 Adobe Commerce 문제를 해결합니다.
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694: *잘못된 상태 변경이 요청됨* 오류로 인해 고객이 주문을 할 수 없음

ACSD-48694 패치를 사용하면 오류가 발생하는 문제가 해결됩니다 *잘못된 상태 변경이 요청됨* 고객이 주문을 할 수 없도록 방지합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치되었습니다. 패치 ID는 ACSD-48694입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

오류 *잘못된 상태 변경이 요청됨* 고객이 주문을 할 수 없도록 방지합니다.

<u>재현 단계</u>:

1. 다음 시간 동안 약간의 지연 추가 `/estimate-shipping-methods` 다음을 포함한 요청: `sleep()` 위치: `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` 함수, 따라서 `/estimate-shipping-methods` 요청이 다음 이후에 완료됨: `/shipping-information` 체크아웃 중에 배송 단계에서 결제 단계로 이동하는 경우.
1. 사용할 세션 구성 [!DNL Redis] (으)로 *disable_locking: 1* 설정.
1. 열기 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** 및 활성화 *[!UICONTROL Persistent Shopping Cart]*.
1. 고객으로 로그인하여 장바구니에 제품을 추가합니다.
1. 고객 세션이 만료되도록 합니다. 영구적 쿠키 및 장바구니는 계속 유지됩니다.
1. 이제 체크아웃으로 이동하여 배송 주소를 추가하고 결제 섹션으로 이동합니다.
1. 홈 페이지 또는 다른 페이지로 돌아가서 고객 계정으로 로그인합니다.
1. 세션이 다시 만료되도록 합니다.
1. 이제 체크아웃 페이지로 바로 이동하여 결제 단계로 이동합니다.
1. 주문해 보세요.

<u>예상 결과</u>:

* 오류가 없습니다.
* 주문이 정상적으로 완료되고 *감사합니다.* 페이지가 표시됩니다.

<u>실제 결과</u>:

오류 *잘못된 상태 변경이 요청됨* 은 표시되지만 주문이 배치됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
