---
title: 'ACSD-51408: 주문 항목 상태가 (으)로 잘못 설정됨 [!UICONTROL backordered]'
description: ACSD-51408 패치를 적용하여 주문 항목 상태가 로 잘못 설정된 Adobe Commerce 문제를 해결합니다. [!UICONTROL backordered].
feature: B2B, Orders
role: Admin
exl-id: 0355beca-4612-438f-8f91-be42d8d637e9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# ACSD-51408: 주문 항목 상태가 (으)로 잘못 설정됨 *[!UICONTROL backordered]*

ACSD-51408 패치를 사용하면 주문 항목 상태가 로 잘못 설정되는 문제가 해결됩니다. [!UICONTROL backordered]. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.33이 설치되었습니다. 패치 ID는 ACSD-51408입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문 항목 상태가 (으)로 잘못 설정되었습니다. *[!UICONTROL backordered]*.

<u>전제 조건</u>:

Adobe Commerce B2B 및 Inventory management(MSI) 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. 새 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. 새 소스를 만듭니다.
1. 1단계에서 생성한 새 웹 사이트에 연결된 새 스톡을 생성하고 2단계에서 생성한 소스를 지정합니다.
1. 회사를 만들고 1단계에서 만든 새 웹 사이트에 할당합니다.
1. 새 고객을 만들고 4단계에서 만든 회사에 할당합니다.
1. 제품을 만들고 새 웹 사이트에 할당한 다음 **[!UICONTROL default stock]** = *0*&#x200B;및 **[!UICONTROL new stock]** 보다 큼 *0*.
1. 사용 **[!UICONTROL backorders]**.
1. 사용 **[!UICONTROL Check/Money Order]** 새로운 웹 사이트 범위에 대한 결제 방법.
1. 활성화 **[!UICONTROL Flat Rate shipping method]** 새 웹 사이트 범위용.
1. 다음 항목에서 새 주문 만들기 **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. 5단계에서 생성된 새 고객을 선택합니다.
1. 1단계에서 만든 새 스토어를 선택합니다.
1. 6단계에서 만든 제품을 선택합니다.
1. 결제 및 배송 방법을 포함한 주문 정보를 작성하십시오.
1. 주문을 제출합니다.
1. 다음 확인: *항목 상태*.

<u>예상 결과</u>

그 상품은 재고에서 발송할 수 있다. 항목 상태는 입니다. *[!UICONTROL ordered]*.

<u>실제 결과</u>

항목 상태는 입니다. *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[주문 항목 상태가 (으)로 잘못 설정됨 *[!UICONTROL Ordered]* 제품 재고가 0인 경우.](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
