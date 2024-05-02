---
title: 'ACSD-47908: *0보다 작거나 같은 값이 필요합니다.* 체크아웃 중 오류가 발생했습니다.'
description: ACSD-47908 패치를 적용하여 Adobe Commerce 오류를 수정합니다 *체크아웃 중 배송 단계에서 소스 및 수량을 선택할 경우 0보다 작거나 같은 값이 예상됩니다*.
exl-id: fec90e4b-9cb8-4cd9-9e85-ccada840c896
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908: *0보다 작거나 같은 값이 필요합니다.* 체크아웃 도중 오류 발생

ACSD-47908 패치를 통해 오류가 해결됩니다 *0보다 작거나 같은 값이 필요합니다.* 체크아웃 중 출하 단계에서 출처와 수량을 선택할 때. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치되었습니다. 패치 ID는 ACSD-47908입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

체크아웃 중 운송 단계에서 출처와 수량을 선택할 때 다음과 같은 오류가 발생합니다. *0보다 작거나 같은 값이 필요합니다.*.

<u>전제 조건</u>:

Adobe Commerce Inventory management(MSI) 모듈을 설치합니다.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** 여러 소스를 구성합니다.
1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** 새 스톡을 생성합니다.
   * 이제 소스를 새 재고에 할당합니다.
1. 다음으로 이동 **[!UICONTROL Catalog]** > **[!UICONTROL Products]** 하나 이상의 제품을 편집합니다.
   * 제품이 새 출처에 할당되었는지 확인하고 사용 가능한 수량을 지정합니다.
1. 다음으로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Orders]** 새 주문을 만듭니다.
1. 그 제품들을 주문에 추가하여 주문합니다.
1. 클릭 **[!UICONTROL Ship]**.
1. 출고할 출처를 선택합니다.
1. 출하할 각 품목의 수량을 지정합니다.
1. 페이지를 다시 로드합니다.
1. 클릭 **[!UICONTROL Proceed to Shipment]**.

<u>예상 결과</u>:

새 배송 페이지가 오류 없이 열립니다.

<u>실제 결과</u>:

* 입력한 수량을 확인할 수 없습니다.
* 다음 오류가 발생합니다. *0보다 작거나 같은 값을 입력하십시오*.

  그러나 오류가 일관되지 않으며 항상 나타나는 것은 아닙니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
