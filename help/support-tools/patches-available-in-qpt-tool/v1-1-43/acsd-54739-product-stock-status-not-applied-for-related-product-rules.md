---
title: 'ACSD-54739: *[!UICONTROL Product Stock]* 상태가 다음에 적용되지 않음 *[!UICONTROL Related Product Rules]*'
description: ACSD-54739 패치를 적용하여 다음과 같은 Adobe Commerce 문제를 해결합니다. *[!UICONTROL Product Stock]* 상태가 다음에 적용되지 않음 *[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
exl-id: 7bc106b1-2c97-46a1-8bb6-71b99511e480
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-54739: *[!UICONTROL Product stock]* 상태가 다음에 적용되지 않음 *[!UICONTROL Related Product Rules]*

ACSD-54739 패치를 사용하면 다음과 같은 문제가 해결됩니다. *[!UICONTROL Product stock]* 상태가 다음에 적용되지 않음 *[!UICONTROL Related Product Rules]*. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43이 설치되었습니다. 패치 ID는 ACSD-54739입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Product stock]* 상태가 다음에 적용되지 않음 *[!UICONTROL Related Product Rules]*.

<u>재현 단계</u>:

1. 설정 **[!UICONTROL Display Out of Stock Products]** 구성 대상 *예*.
1. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** 및 설정 *예* 프로모션 규칙 조건.
1. 관련 제품 규칙을 만듭니다. 다음으로 이동 **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > 속성 수량을 사용하여 조건을 추가합니다(재고/재고 부족 선택).
1. 프론트엔드에 있는 제품들을 확인하세요

<u>예상 결과</u>:

재고/재고 부족 제품 일치 기준 *[!UICONTROL Related Product Rules]*.

<u>실제 결과</u>:

재고/재고 부족 제품이 *[!UICONTROL Related Product Rules]*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
