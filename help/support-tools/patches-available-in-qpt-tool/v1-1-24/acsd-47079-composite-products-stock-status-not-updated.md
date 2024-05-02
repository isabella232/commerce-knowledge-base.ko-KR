---
title: "ACSD-47079: 하위 제품 재고 상태가 변경될 때 복합 제품의 재고 상태가 업데이트되지 않음"
description: ACSD-47079 패치를 적용하여 REST API POST /rest/V1/inventory/source-items를 통해 하위 제품 재고 상태가 변경될 때 합성 제품(번들, 그룹화 및 구성 가능한) 재고 상태가 업데이트되지 않는 Adobe Commerce 문제를 수정합니다.
exl-id: 603e4548-fb04-43b4-a033-4f2c7f665fae
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-47079: 하위 제품 재고 상태가 변경될 때 복합 제품의 재고 상태가 업데이트되지 않음

ACSD-47079 패치는 하위 제품 스톡 상태가 REST API POST을 통해 변경되면 복합 제품(번들, 그룹화 및 구성 가능)의 스톡 상태가 업데이트되지 않는 문제를 수정합니다 `/rest/V1/inventory/source-items`. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되었습니다. 패치 ID는 ACSD-47079입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

하위 제품 재고 상태가 REST API POST을 통해 변경되면 복합 제품(번들, 그룹화 및 구성 가능)의 재고 상태가 업데이트되지 않습니다 `/rest/V1/inventory/source-items`.

<u>재현 단계</u>:

1. 각 구성 가능하고 번들로 묶인 그룹화된 제품을 간단한 하위 제품 하나로 만듭니다.
1. 각 단순 하위 제품 상태를 다음으로 설정 **[!UICONTROL Out of Stock]** 사용 `source-items` API 호출.
1. 이제 상위 제품의 재고 상태를 확인합니다.

<u>예상 결과</u>:

상위 제품의 상태는 입니다. [!UICONTROL Out of Stock].

<u>실제 결과</u>:

상위 제품의 상태는 입니다. [!UICONTROL In Stock].

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
