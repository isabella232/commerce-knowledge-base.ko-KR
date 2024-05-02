---
title: 'ACSD-53925: 다음을 사용하여 CMS 블록을 저장할 수 없음: [!UICONTROL Product Carousel]'
description: '''catalog_product_price''에 대한 차원 모드가 웹 사이트로 설정된 경우 관리자가 제품 캐러셀에 CMS 블록을 저장할 수 없는 Adobe Commerce 문제를 해결하려면 ACSD-53925 패치를 적용합니다.'
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: 6ef6d8ff-4ebb-4adb-9fb7-0d4a81a25f50
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-53925: CMS 블록을 저장할 수 없음 *[!UICONTROL Product Carousel]*

ACSD-53925 패치를 사용하면 관리자가 로 CMS 블록을 저장할 수 없는 문제가 해결됩니다. *[!UICONTROL Product Carousel]* 다음에 대한 차원 모드: `catalog_product_price` 을 웹 사이트로 설정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.43이 설치되었습니다. 패치 ID는 ACSD-53925입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자가 다음으로 CMS 블록을 저장할 수 없음 *[!UICONTROL Product Carousel]* 다음에 대한 차원 모드: `catalog_product_price` 을 웹 사이트로 설정합니다.

<u>재현 단계</u>:

1. 두 가지 간단한 제품을 만듭니다.
   * simple1 - $10
   * simple2 - $20
1. 번들 제품 만들기 &#39;*bundle1-dyn*&#39; 간단한 제품 SKU를 기반으로 하는 두 가지 옵션이 있습니다.
1. 제품 가격 인덱서에 대한 차원 모드 설정:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. 다음으로 이동 **[!UICONTROL Content]** > **[!UICONTROL Blocks]**&#x200B;을 클릭하고 새 CMS 블록을 만듭니다.
1. 다음을 사용하여 콘텐츠 편집 [!DNL Page Builder]:
   * 추가 *[!UICONTROL Row]* 요소
   * 추가 *[!UICONTROL Products]* 요소
   * 선택 *[!UICONTROL Product Carousel]*
   * 제품 SKU 입력 - *bundle1-dyn*
1. CMS 블록을 저장합니다.

<u>예상 결과</u>:

사용자는 오류 없이 제품 캐러셀을 추가할 수 있습니다.

<u>실제 결과</u>:

* UI에 메시지가 표시됩니다. *죄송합니다. 이 콘텐츠를 생성하는 동안 오류가 발생했습니다.*
* `var/log/exception.log` 에는 다음 오류가 포함되어 있습니다.

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
