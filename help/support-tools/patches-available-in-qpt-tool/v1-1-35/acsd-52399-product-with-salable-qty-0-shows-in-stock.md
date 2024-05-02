---
title: 'ACSD-52399: 판매 가능한 수량이 0인 제품이 재고로 표시됨'
description: ACSD-52399 패치를 적용하여 Adobe Commerce 문제를 해결합니다. 구성 가능한 제품 옵션이 판매 가능한 수량이 0인 경우 제품 페이지에서 *재고 있음*이 표시됩니다.
feature: Products, Configuration
role: Admin, Developer
exl-id: 3c9e6edd-f7ce-492e-b74f-68354d8e2633
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52399: 판매 가능한 수량 0이 있는 제품이 재고로 표시됨

ACSD-52399 패치는 판매 가능 수량이 영(0)인 구성 가능한 제품 옵션이 표시되는 문제를 해결합니다 *재고 있음* 제품 페이지에서 참조할 수 있습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있습니다. 패치 ID는 ACSD-52399입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

판매 가능 수량이 영(0)인 구성 가능한 제품 옵션이 다음을 표시합니다. *재고 있음* 제품 페이지에서 참조할 수 있습니다.

<u>재현 단계</u>:

1. 0(판매 가능 수량) 제품 옵션을 사용하여 구성 가능한 제품을 만듭니다.
1. 상점 첫 화면의 제품 페이지로 이동하여 구성 가능한 제품을 선택하고 변형/구성을 확인합니다.
1. 선택 **[!UICONTROL Add to Cart]**.

<u>예상 결과</u>:

*[!UICONTROL Add to Cart]* 선택할 때는 버튼을 사용할 수 없습니다. *품절* 제품 구성.

<u>실제 결과</u>:

구성 가능한 변형은 상점 첫 화면에서 사용할 수 있으며 선택한 후 장바구니에 추가할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
