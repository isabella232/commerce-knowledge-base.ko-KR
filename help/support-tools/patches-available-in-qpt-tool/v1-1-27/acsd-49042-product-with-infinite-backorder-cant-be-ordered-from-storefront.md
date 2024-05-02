---
title: "ACSD-49042: 무한 역주문의 제품은 상점에서 주문할 수 없습니다."
description: ACSD-49042 패치를 적용하여 무한 역주문이 있는 제품을 상점 전면에서 주문할 수 없는 Adobe Commerce 문제를 해결합니다.
exl-id: b9227296-f300-447c-a241-30ccc0691c9a
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042: 무한 주문된 제품은 상점에서 주문할 수 없습니다.

ACSD-49042 패치는 백오더가 무한한 제품을 상점 앞에서 주문할 수 없는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치되었습니다. 패치 ID는 ACSD-49042입니다. 이 문제는 Adobe Commerce 2.4.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

백오더가 무한한 제품을 상점에서 주문할 수 없을 때 오류가 발생합니다.

<u>재현 단계</u>:

1. 다음 구성 설정을 설정합니다.
   * **[!UICONTROL Display Out of Stock Products]** 을 로 설정 *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** 을 로 설정 *[!UICONTROL Allow Qty Below 0]*.
1. 새 항목 추가 **[!DNL custom stock]** 및 **[!DNL custom source]**.
1. 에 제품 할당 **[!DNL custom source]** 재고 번호가 설정되어 있는지 확인합니다(예: *10*).
1. 제품 편집 페이지에서 를 엽니다. **[!UICONTROL Advanced Inventory]**. 설정 **[!UICONTROL minimum quantity]** 장바구니에서 (예: *160*). 수량은 재고보다 많아야 한다.
1. 상점에 가셔서 예약하실 상품을 구매하세요.
1. 변경 **[!UICONTROL product quantity]** 끝 *0*. 중요한 점은 의 제품을 저장하는 것입니다. **[!DNL Admin panel]** 예약 사항이 있을 때
1. 를 엽니다. **[!UICONTROL product page]** 상점 앞에서 제품을 장바구니에 추가해 보십시오.

<u>예상 결과</u>:

아래 수량에 대한 미납주문 때문에 제품을 장바구니에 추가할 수 있습니다. *0* 허용됩니다.

<u>실제 결과</u>:

그 상품은 품절로 진열되어 있다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
