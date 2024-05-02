---
title: '"ACSD-53750: 다중 스레드 catalog_product_price 리인덱스 도중 "끊어진 파이프 또는 닫힌 연결" 오류 발생"'
description: ACSD-53750 패치를 적용하여 다중 스레드 catalog_product_price 재인덱싱 도중 *파이프가 끊기거나 연결이 닫히는* 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: afb30384-74e7-4857-9aff-8e99f5abc309
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-53750: *끊어진 파이프 또는 닫힌 연결* 다중 스레드 도중 오류 발생 `catalog_product_price` 색인 재지정

ACSD-53750 패치는 *끊어진 파이프 또는 닫힌 연결* 다중 스레드 도중 오류 발생 `catalog_product_price` 색인 재지정. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.37이 설치되었습니다. 패치 ID는 ACSD-53750입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*끊어진 파이프 또는 닫힌 연결* 다중 스레드 도중 오류 발생 `catalog_product_price` 색인 재지정.

<u>재현 단계</u>:

1. RabbitMq를 구성합니다.
1. 첨부된 를 사용하여 샘플 데이터 생성 `small.xml` 파일.
1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** 및 설정 **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. 이를 지원하는 인덱스에 대한 차원 모드를 설정합니다. 예: `catalog_product_price_website_and_customer_group` 또는 `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. 다음에 대한 인덱서 재설정 실행: `catalog_product_price`.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. 여러 스레드를 사용하여 인덱서 재설정에 대해 인덱서를 실행합니다.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>예상 결과</u>:

오류가 발생하지 않습니다.

<u>실제 결과</u>:

AMQP 연결에 의해 다음 오류가 발생합니다. *끊어진 파이프 또는 닫힌 연결*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
