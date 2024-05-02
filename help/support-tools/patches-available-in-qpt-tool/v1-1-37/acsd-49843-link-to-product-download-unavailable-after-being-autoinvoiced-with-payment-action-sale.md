---
title: 'ACSD 49843: 제품 다운로드 링크가 다음 주소로 자동 청구된 후 사용할 수 없음 [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: 다음과 같은 경우 ACSD-49843 패치를 적용하여 온라인 결제 방법으로 주문 품목이 자동 인보이스 발행된 후 제품 다운로드 링크를 사용할 수 없는 Adobe Commerce 문제를 해결합니다. [!UICONTROL Payment Action] 이(가) (으)로 설정됨 [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843: 제품 다운로드 링크가 다음 주소로 자동 청구된 후 사용할 수 없음 [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

ACSD-49843 패치는 다음과 같은 경우 온라인 결제 방법으로 주문된 항목의 청구서가 자동 발행된 후 제품 다운로드 링크를 사용할 수 없는 문제를 해결합니다. [!UICONTROL Payment Action] 이(가) (으)로 설정됨 [!UICONTROL Intent Sale]. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.37이 설치되었습니다. 패치 ID는 ACSD-49843입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음과 같은 경우에는 온라인 결제 방법으로 주문된 항목에 자동 송장이 발행된 후 제품 다운로드 링크를 사용할 수 없습니다. [!UICONTROL Payment Action] 이(가) (으)로 설정됨 [!UICONTROL Intent Sale].

<u>재현 단계</u>:

1. Adobe Commerce 관리자에 로그인하고 다음으로 이동합니다. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * 다음에서 [!UICONTROL Payment Action] 드롭다운, 선택 **[!UICONTROL Intent Sale]**, 및 설정 *[!UICONTROL Enable Card Payments]* 끝 *예*.

1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]**, 및 가 로 설정되어 있는지 확인합니다. *&quot;인보이스 발행&quot;*.
1. 상점에서 고객으로 로그인합니다.

   * 다운로드 가능한 제품과 간단한 제품을 장바구니에 추가합니다.
   * 사용 [!DNL Braintree Pay] 카드 옵션을 사용하여 주문합니다.

1. 다음으로 이동 **[!UICONTROL My Orders]** 주문에 대해 송장이 자동으로 생성되는지, 그리고 두 품목 상태가 모두 *&quot;인보이스 발행&quot;*.
1. 다음으로 이동 **[!UICONTROL My Downloadable Products]** 다운로드 링크를 아직 사용할 수 없는지 확인합니다.
1. 관리자에서 해당 주문으로 이동하여 해당 배송을 생성합니다.
1. 상점 앞에서 **[!UICONTROL My Downloadable Products]** 이제 다운로드 링크를 사용할 수 있는지 확인합니다.

<u>예상 결과</u>:

다운로드 링크는 다운로드 가능한 제품 상태가 인 경우 사용할 수 있습니다. *&quot;인보이스 발행&quot;*.

<u>실제 결과</u>:

다운로드 가능한 제품 상태에 이 표시되어 있어도 다운로드 링크를 사용할 수 없습니다 *&quot;인보이스 발행&quot;*. 실제 제품에 대한 선적이 생성된 후에만 사용할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
