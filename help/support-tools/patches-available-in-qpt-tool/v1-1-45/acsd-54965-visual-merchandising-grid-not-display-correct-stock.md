---
title: 'ACSD-54965: [!UICONTROL Visual Merchandising] 격자에 올바른 재고가 표시되지 않음'
description: ACSD-54965 패치를 적용하여 다음과 같은 Adobe Commerce 문제를 해결합니다. [!UICONTROL Visual Merchandising] 제품이 사용자 정의 스톡에 할당될 때 그리드에 올바른 스톡이 표시되지 않습니다.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: 13d98f55-ca2c-4064-b66f-ab2cdeb37382
source-git-commit: 4f05117aa42dec1f56e4986ffd22d1a68bf5cea2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965: [!UICONTROL Visual Merchandising] 격자에 올바른 재고가 표시되지 않습니다.

ACSD-54965 패치를 사용하면 다음과 같은 문제가 해결됩니다. [!UICONTROL Visual Merchandising] 제품이 사용자 정의 스톡에 할당될 때 그리드에 올바른 스톡이 표시되지 않습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45가 설치되어 있습니다. 패치 ID는 ACSD-54965입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음 [!UICONTROL Visual Merchandising] 제품이 사용자 정의 스톡에 할당될 때 그리드에 올바른 스톡이 표시되지 않습니다.

<u>재현 단계</u>:

1. 새 소스를 만듭니다.
1. 새 재고를 생성합니다.
1. 다음 두 가지 제품을 만듭니다.
   * 사용자 정의 재고가 있는 하나의 제품만.
   * 기본 재고가 있는 하나의 제품만.
1. 이 제품을 범주에 추가합니다.
1. 로 이동 [!UICONTROL visual Merchandising] 격자 (*[!UICONTROL Products in Category]*).

<u>실제 결과</u>:

다음에서 *[!UICONTROL All Store Views]* 범위, 사용자 지정 스톡이 있는 제품에 수량이 표시되지 않습니다. 다음 경우에만 해당 *[!UICONTROL Default Store View]* 범위가 선택되어 있으면 사용자 정의 스톡에 제품의 수량이 표시됩니다.

<u>예상 결과</u>:

범위가 다음과 같은 경우 격자에 모든 스톡 정보가 표시됩니다. *[!UICONTROL All Store Views]*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
