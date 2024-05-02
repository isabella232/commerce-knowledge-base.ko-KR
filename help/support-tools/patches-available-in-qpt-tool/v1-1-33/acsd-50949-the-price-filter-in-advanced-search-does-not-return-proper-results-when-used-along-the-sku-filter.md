---
title: "ACSD-50949: 고급 검색의 가격 필터가 SKU 필터와 함께 사용될 때 적절한 결과를 반환하지 않음"
description: ACSD-50949 패치를 적용하여 고급 검색의 가격 필터가 SKU 필터와 함께 사용될 때 적절한 결과를 반환하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Search
role: Admin
exl-id: 3e1f88dc-07f6-4e10-b4b7-163648076cbc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 1%

---

# ACSD-50949: 고급 검색의 가격 필터가 SKU 필터와 함께 사용할 때 적절한 결과를 반환하지 않음

ACSD-50949 패치는 고급 검색의 가격 필터가 SKU 필터와 함께 사용될 때 적절한 결과를 반환하지 않는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33이 설치되었습니다. 패치 ID는 ACSD-50949입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 문제

고급 검색의 가격 필터는 SKU 필터와 함께 사용할 때 적절한 결과를 반환하지 않습니다.

<u>재현 단계</u>:

1. 다음과 같은 여러 제품을 만듭니다.

   | SKU | 이름 | 가격 | 수량 |
   |-----|-----------|-------|----------|
   | MJ1 | 제품 1 | 10달러 | 10 |
   | MJ2 | 제품 2 | 15달러 | 10 |
   | MJ3 | 제품 3 | 21달러 | 10 |
   | MJ4 | 제품 4 | 32달러 | 10 |
   | MJ5 | 제품 5 | 33달러 | 10 |
   | MJ6 | 제품 6 | US$34 | 10 |
   | MJ7 | 제품 7 | 44달러 | 10 |

1. 를 엽니다. **[!UICONTROL Advanced Search]** 상점 첫 화면에서 SKU로 검색: &quot;MJ&quot;.
1. 다음을 클릭합니다. **[!UICONTROL Modify your search]** 링크를 클릭합니다.
1. 의 기준에 가격 범위를 추가합니다. *1* 끝 *21*&#x200B;을(를) 클릭하고 **[!UICONTROL Search]** 단추를 클릭합니다.

<u>예상 결과</u>:

가격이 정의된 범위의 제품만 반환됩니다.

<u>실제 결과</u>:

가격이 보다 높은 제품 *21달러* 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 다음에서 [!DNL Quality Patches Tool] 가이드.
