---
title: 'ACSD-57394: 의 여러 정렬 속성별로 잘못된 제품 정렬 [!DNL GraphQL]'
description: ACSD-57394 패치를 적용하여에서 여러 정렬 속성을 사용할 때 제품이 잘못 정렬되는 Adobe Commerce 문제를 수정합니다 [!DNL GraphQL].
feature: GraphQL, Products
role: Admin, Developer
exl-id: f2e24daa-43a0-46b2-80b2-4e0ee116b776
source-git-commit: 42712af2ce4337cd64b8dea555139e4252fb91cf
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-57394: 의 여러 정렬 속성별로 잘못된 제품 정렬 [!DNL GraphQL]

ACSD-57394 패치는에서 여러 정렬 속성을 사용할 때 제품이 잘못 정렬되는 문제를 해결합니다 [!DNL GraphQL]. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48이 설치되었습니다. 패치 ID는 ACSD-57394입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

에서 여러 정렬 속성을 사용할 때 제품이 잘못 정렬됨 [!DNL GraphQL].

<u>재현 단계</u>:

1. 가격과 이름이 다른 제품을 몇 개 만듭니다.
1. 카테고리를 만들고 만든 제품을 카테고리에 할당합니다.
1. 보내기 [!DNL GraphQL] products 쿼리에서 몇 가지 기능이 있는 생성된 범주 *sort* 속성. For example:

   ```
   {
   products(
     currentPage: 1
     pageSize: 10
     filter: {
       category_id: {
         eq :"3"
       }
     }
     sort: {  price: DESC, name: ASC, position: ASC
     }
   ){
   items{
     name
     sku
   
       price_range {
           minimum_price {
   
         regular_price {
           value
           currency
         }
         final_price {
           value
           currency
         }
         discount {
           amount_off
           percent_off
         }
               }
           }
      }
     }
    }
   ```

1. 생성 후 응답 확인 *sort* 속성.

<u>예상 결과</u>:

제품은 올바른 순서로 반품되어야 합니다. 여러 특성별로 제품을 정렬하는 것이 좋습니다.

<u>실제 결과</u>:

제품이 올바른 순서로 반송되지 않습니다. 여러 특성별로 제품을 정렬하는 것은 작동하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.

