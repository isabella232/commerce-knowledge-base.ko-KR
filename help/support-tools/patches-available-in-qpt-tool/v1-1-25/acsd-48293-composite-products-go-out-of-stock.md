---
title: 'ACSD-48293: 재입고된 아동용 제품 판매 시 품절 된 복합 제품'
description: ACSD-48293 패치를 적용하여 품절된 하위 제품이 재고로 반환될 때 합성 제품이 품절되는 Adobe Commerce 문제를 해결합니다.
exl-id: 74ca34fe-e015-4daf-a608-4756c8ab3558
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48293: 재입고된 어린이 제품이 품절되었을 때 재고 부족 복합 제품

ACSD-48293 패치는 품절된 하위 제품이 재고로 반환될 때 복합 제품이 품절되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25가 설치되어 있습니다. 패치 ID는 ACSD-48293입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다 팔린 아동용품을 재고로 반품하면 복합제품은 품절됩니다.

<u>재현 단계</u>:

1. 보조 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. 두 개의 소스와 재고를 만들어 각 웹 사이트에 할당합니다.
1. 아래에서 품절 제품 표시 옵션을 활성화합니다. **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. 기본 웹 사이트의 재고 출처(수량 = 1 설정)를 사용하여 하나의 연관된 제품으로 구성 가능한 제품을 생성합니다.
1. 구성 가능한 제품을 주문합니다.
1. 크론을 작동시키세요
1. 상점에서 구성 가능한 제품을 열고 재고가 없는지 확인합니다.
1. 에서 구성 가능한 제품을 엽니다. [!UICONTROL Admin] 및 설정 **[!UICONTROL Manage Stock Option]** 끝 *[!UICONTROL No]*.
1. 크론을 작동시키세요
1. 주문을 출하하고 수량을 간단한 제품에 추가하여 재고를 만듭니다.
1. 크론을 작동시키세요
1. 상점에서 제품 사용 가능 여부를 확인합니다.

<u>예상 결과</u>:

구성 가능한 제품이 재고에 있습니다.

<u>실제 결과</u>:

구성 가능한 제품의 재고가 부족합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
