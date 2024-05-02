---
title: "ACSD-51683: 사용자 지정 가능한 옵션은 GraphQL을 사용하여 장바구니에 추가할 수 없음"
description: ACSD-51683 패치를 적용하여 사용자 지정 가능한 옵션을 GraphQL을 사용하여 장바구니에 추가할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL
role: Admin
exl-id: 4de0d8b7-714e-4bbf-8a0d-bb6e0c3aae55
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51683: 사용자 지정 가능한 옵션은 GraphQL을 사용하여 장바구니에 추가할 수 없습니다.

ACSD-51683 패치는 사용자 지정 가능한 옵션을 GraphQL을 사용하여 장바구니에 추가할 수 없는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35가 설치되어 있습니다. 패치 ID는 ACSD-51683입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자 지정 가능한 옵션은 GraphQL을 사용하여 장바구니에 추가할 수 없습니다.

<u>재현 단계</u>:

1. 맞춤화가 가능한 간단한 제품 만들기 **텍스트 필드** 옵션을 선택합니다.
1. [장바구니에 추가](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) GraphQL을 통해 필요한 사용자 지정 가능 옵션이 있는 생성된 제품입니다.
1. 보내기 [장바구니](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) GraphQL이 장바구니에서 제품 및 해당 세부 사항을 확인하도록 요청합니다.

<u>예상 결과</u>

다음 `Customizable_options` GraphQL 응답의 섹션에는 제품을 장바구니에 추가하는 동안 제공된 데이터가 포함됩니다.

<u>실제 결과</u>

다음 `Customizable_options` GraphQL 응답의 섹션이 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
