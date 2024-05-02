---
title: 'ACSD-46767: [!UICONTROL Category] 재고 수량이 변경되면 페이지가 무효화됨'
description: ACSD-46767 패치를 적용하여 다음과 같은 Adobe Commerce 문제를 해결합니다. [!UICONTROL Category] 제품이 아직 재고가 있는 경우에도 재고 수량이 변경되면 페이지가 무효화됩니다.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 39811c03-8518-4975-a128-31537b4706c0
source-git-commit: b7e2ff7cd259963adb9a113eb8e94acdaa45ba1e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category] 재고 수량이 변경되면 페이지 캐시가 무효화됨

ACSD-46767 패치를 사용하면 다음과 같은 문제가 해결됩니다. [!UICONTROL Category] 제품이 아직 재고가 있는 경우에도 재고 수량이 변경되면 페이지가 무효화됩니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46이 설치되었습니다. 패치 ID는 ACSD-46767입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Category] 재고 수량이 변경되면 페이지가 무효화됩니다.

<u>재현 단계</u>:

1. 몇 가지 제품을 만들고 동일한 카테고리에 추가합니다.
1. 를 엽니다. *[!UICONTROL Category]* 페이지가 캐시되도록 상점 첫 화면의 페이지입니다.
1. 범주에 있는 제품 중 하나를 주문합니다. *(제품 수량은 변경되었지만 제품은 아직 재고가 있습니다.)*.
1. 를 엽니다. [!UICONTROL Category] 다시 가게 앞에 페이지를 올려 놓으세요.

<u>실제 결과</u>:

페이지가 캐시에서 로드되지 않습니다. 다시 생성됩니다.

<u>예상 결과</u>:

페이지가 캐시에서 로드됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
