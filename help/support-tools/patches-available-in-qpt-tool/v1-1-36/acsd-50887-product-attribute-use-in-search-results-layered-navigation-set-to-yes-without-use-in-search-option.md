---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* (* 없이 예로 설정)[!UICONTROL Use in Search]* 옵션'
description: ACSD-50887 패치를 적용하여 제품 속성 속성이 *인 Adobe Commerce 문제를 해결합니다.[!UICONTROL Use in Search Results Layered Navigation]* * 없이 *예*로 설정할 수 있습니다.[!UICONTROL Use in Search]* 옵션도 *예*로 설정됩니다.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* 을 로 설정 *예* 없이 *[!UICONTROL Use in Search]* 옵션

ACSD-50887 패치는 제품 속성 속성 의 문제를 해결합니다 *[!UICONTROL Use in Search Results Layered Navigation]* 을 로 설정할 수 있습니다. *예* 없이 *[!UICONTROL Use in Search]* 옵션도 (으)로 설정됨 *예*. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.36이 설치되었습니다. 패치 ID는 ACSD-50887입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 속성 속성 *[!UICONTROL Use in Search Results Layered Navigation]* 을 로 설정할 수 있습니다. *예* 없이 *[!UICONTROL Use in Search]* 옵션도 (으)로 설정됨 *예*.

이러한 설정은 함께 사용하도록 설계되었습니다. 패치를 적용한 상태에서 *[!UICONTROL Use in Search]* 옵션이 로 설정되어 있습니다. *아니요*, *[!UICONTROL Use in Search Results Layered Navigation]* 옵션이 로 설정된 것처럼 작동하도록 옵션이 숨겨져 있습니다. *아니요*.

<u>재현 단계</u>:

1. 관리자에서 다음 위치로 이동합니다. **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** 다중 선택 유형으로 속성을 만들고 다음을 설정합니다.

   * *[!UICONTROL Use in Search]= 아니요*
   * *[!UICONTROL Use in Layered Navigation]= (모든 옵션)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= 예*
   * *이름 = Test_attribute*
   * *옵션*:
      * *스티커*
      * *선택기*

1. 기본 속성 집합에 새 속성을 추가합니다.
1. 다음 두 가지 제품을 만듭니다.

   1. 첫 번째 제품:
      * 이름 = 스티커
      * 가격, 수량, 중량을 1로 설정
      * Test_attribute = 옵션 선택 *스티커*

   1. 두 번째 제품:
      * 이름 = 선택기
      * 가격, 수량, 중량을 1로 설정
      * Test_attribute = 두 옵션 모두 선택

1. 실행 `catalogsearch_fulltext` 색인 재지정:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. 단어로 검색 *스티커* 가게 앞에서요

<u>예상 결과</u>:

제품만 *스티커* 다음 이유로 반환됩니다. [!DNL Elasticsearch] 다음과 같은 경우에는 Test_attribute를 인덱싱하지 않습니다. *[!UICONTROL Use in Search]* 이(가) (으)로 설정되었습니다. *아니요*.

<u>실제 결과</u>:

두 제품 모두 반품됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
