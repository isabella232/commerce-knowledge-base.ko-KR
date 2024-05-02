---
title: 'ACSD-57315: 새 트랜잭션이에 생성됨 [!DNL PayPal Payflow Pro] 가져오기 단추를 클릭할 때마다'
description: ACSD-57315 패치를 적용하여 새 트랜잭션이 작성되는 Adobe Commerce 문제를 해결합니다. [!DNL PayPal Payflow Pro] 의 트랜잭션 보기 화면에서 가져오기 단추를 클릭할 때마다 [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
source-git-commit: b7f85e4fdb7ef4a6328a1a411dac765dd8da083e
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: 새 트랜잭션이에 생성됨 [!DNL PayPal Payflow Pro] 가져오기 단추를 클릭할 때마다

ACSD-57315 패치는에서 새 트랜잭션이 만들어지는 문제를 해결합니다. [!DNL PayPal Payflow Pro] 의 트랜잭션 보기 화면에서 가져오기 단추를 클릭할 때마다 [!UICONTROL Admin]. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.48이 설치되었습니다. 패치 ID는 ACSD-57315입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

새 거래가에 생성됩니다. [!DNL PayPal Payflow Pro] 의 트랜잭션 보기 화면에서 가져오기 단추를 클릭할 때마다 [!UICONTROL Admin].

<u>재현 단계</u>:

1. 구성 [!DNL PayPal Payflow Pro].
1. 거래 방법을 다음으로 설정 *[!UICONTROL Sale]*.
1. 다음을 사용하여 주문 *신용 카드*.
1. 다음에서 트랜잭션을 엽니다. [!UICONTROL Admin].
1. 을(를) 클릭합니다 **[!UICONTROL Fetch]** 단추를 클릭합니다.
1. 확인 [!DNL PayPal] 주문과 관련된 거래에 대한 계정.

<u>예상 결과</u>:

신규 결제 거래가 생성되지 않습니다.

<u>실제 결과</u>:

이미 지급된 주문에 대해 신규 지급 거래가 생성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
