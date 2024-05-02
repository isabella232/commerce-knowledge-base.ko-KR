---
title: '[!DNL ACSD-47280]: 공유 카탈로그 비활성화가 잘못된 제품 검색 결과를 제공함'
description: 적용 [!DNL ACSD-47280] 공유 카탈로그 기능이 비활성화되었을 때 올바른 검색 결과가 표시되는 문제를 해결하기 위한 패치입니다.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: 공유 카탈로그를 비활성화하면 잘못된 제품 검색 결과가 표시됩니다

다음 [!DNL ACSD-47280] patch는 [!DNL shared catalog] 기능이 비활성화되었습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22가 설치되었습니다. 다음 [!DNL patch ID] 은(는) [!DNL ACSD-47280]. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**
* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 사용 [!DNL patch ID] 를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

비활성화 중 [!DNL shared catalog] 이(가) 잘못된 제품 검색 결과를 제공합니다.

<u>전제 조건</u>:

* [!DNL B2B] 설치된 모듈

<u>재현 단계</u>:

1. 두 번째 웹 사이트를 만듭니다.
1. 두 번째 웹 사이트에 제품을 할당합니다.
1. 에서 제품 확인 **두 번째 웹 사이트** 사용 [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. 사용 **[!UICONTROL Shared Catalog]** 기본 [!DNL scope].
1. 다음 [!DNL GraphQL] 요청은 더 이상 두 번째 웹 사이트에 대한 제품을 표시하지 않으며, 이는 올바른 결과입니다.
1. 로 이동 [!DNL scope] / 두 번째 웹 사이트 및 비활성화 **[!UICONTROL Company]**.

<u>예상 결과</u>:

다음 [!DNL GraphQL] 요청에도 두 번째 웹 사이트에 대한 제품이 표시됩니다.

<u>실제 결과</u>:

다음 [!DNL GraphQL] 요청에는 두 번째 웹 사이트에 대한 제품이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
