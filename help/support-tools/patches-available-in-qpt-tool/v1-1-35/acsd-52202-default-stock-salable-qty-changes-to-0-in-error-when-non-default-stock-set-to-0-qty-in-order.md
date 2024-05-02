---
title: 'ACSD-52202: 기본 재고 판매 가능 수량이 0으로 변경되고, 비기본 재고가 순번대로 0으로 설정된 경우 오류가 발생합니다.'
description: ACSD-52202 패치를 적용하여 주문에서 기본값이 아닌 재고가 0으로 설정될 때 기본 재고 판매 수량이 오류로 인해 0으로 변경되는 Adobe Commerce 문제를 수정합니다.
feature: Inventory, Products
role: Admin
exl-id: 8a3b5da4-cf16-41c8-b2d5-b740d638c745
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52202: 주문에서 비기본 재고가 0 수량으로 설정된 경우 기본 재고 판매 수량이 0으로 잘못 변경됩니다.

ACSD-52202 패치는 주문에서 기본값이 아닌 재고가 0으로 설정될 때 기본 재고 판매 가능 수량(수량)이 오류로 인해 0으로 변경되는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있습니다. 패치 ID는 ACSD-52202입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문에서 기본 재고가 아닌 재고가 0 수량으로 설정된 경우 기본 재고 판매 수량이 0으로 잘못 변경됩니다.

<u>재현 단계</u>:

1. 에 로그인합니다 [!DNL Admin].
1. 만들기 **website2**.
1. 사용자 지정 만들기 **source2**.
1. 사용자 지정 만들기 **stock2**.
1. 할당 **source2** 및 **stock2** 끝 **website1** 기본 웹 사이트에 기본 소스 및 재고를 추가합니다.
1. 간단한 제품 만들기 및 할당 **수량** = *10* 기본 소스 및 **수량** = *1* 대상: **source2** 소스.
1. 다음을 사용하여 주문 **수량** = *1* 대상 **website2**.
1. 송장 및 선적을 생성합니다.
1. 간단한 제품 확인 **판매 가능 수량**.

<u>예상 결과</u>:

다음 **판매 가능 수량** = *10* 대상 **source2**.

<u>실제 결과</u>:

다음 **판매 가능 수량** = *0* 두 소스 모두에 사용할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
