---
title: '''ACSD-54989: 다음 경우에 회사 관리자가 주문할 수 없음: [!UICONTROL Enable Purchase Orders] 예 및 로 설정 [!UICONTROL Purchase Order] 아니요로 설정'
description: ACSD-54989 패치를 적용하여 다음과 같은 경우 회사 관리자가 주문할 수 없는 Adobe Commerce 문제를 해결합니다. [!UICONTROL Enable Purchase Orders] 이 예로 설정되어 있고 [!UICONTROL Purchase Order] 이 아니요로 설정되어 있습니다.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: c2850409-d310-4681-80ec-af8ba347854c
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54989: 다음 경우에 회사 관리자가 주문할 수 없음: *[!UICONTROL Enable Purchase Orders]* 을 로 설정 *예* 및 *[!UICONTROL Purchase Order]* 을 로 설정 *아니요*

ACSD-54989 패치는 다음과 같은 경우 주문을 할 수 없는 문제를 해결합니다. **[!UICONTROL Enable Purchase Orders]** 을 로 설정 *예* 및 **[!UICONTROL Purchase Order]** 을 로 설정 *아니요*. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40이 설치되었습니다. 패치 ID는 ACSD-54989입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음과 같은 경우에는 회사 관리자가 주문을 할 수 없습니다. **[!UICONTROL Enable Purchase Orders]** 이(가) (으)로 설정됨 *예* 및 **구매 주문** 을 로 설정 *아니요*.

<u>전제 조건</u>:

설치 [!DNL B2B] 모듈.

<u>재현 단계</u>:

1. 회사 및 나가기 사용 [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *아니요*.
1. 가격이 100인 간단한 제품을 만듭니다.
1. 관리자를 통해 새 회사를 만듭니다.
1. 설정 [!UICONTROL **구매 주문 활성화**] 끝 *예*.
1. 상점 첫 화면에서 회사 관리자로 로그인합니다.
1. 생성된 간단한 제품을 장바구니에 추가합니다.
1. 체크아웃 페이지로 이동하고 **[!UICONTROL Place Order]** 구매를 완료합니다.

<u>예상 결과</u>:

정상적으로 주문할 수 있습니다.

<u>실제 결과</u>:

다음 **[!UICONTROL My Account]** 페이지가 열리고 순서가 지정되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
