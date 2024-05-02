---
title: '''ACSD-56415: 성능 [!UICONTROL Partial Price Indexing] ''DELETE'' 쿼리로 인해 느려짐'
description: ACSD-56415 패치를 적용하여 의 성능이 저하되는 Adobe Commerce 문제를 해결합니다. [!UICONTROL Partial Price Indexing] 데이터베이스에 색인화할 부분 가격 데이터가 많을 때 'DELETE' 쿼리로 인해 이 느려집니다.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415: 성능 [!UICONTROL Partial Price Indexing] 다음 이유로 인해 속도가 느려집니다. `DELETE` 쿼리

ACSD-56415 패치는 의 성능이 [!UICONTROL Partial Price Indexing] 다음 이유로 인해 속도가 느려집니다. `DELETE` 데이터베이스에 부분 가격 데이터 인덱스가 많은 경우 쿼리합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45가 설치되어 있습니다. 패치 ID는 ACSD-56023입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

의 성능 [!UICONTROL Partial Price Indexing] 다음 이유로 인해 속도가 느려집니다. `DELETE` 데이터베이스에 부분 가격 데이터 인덱스가 많은 경우 쿼리합니다.

<u>재현 단계</u>:

1. 만들기 *300000 제품* 및 *10개 웹 사이트* 큰 성능 프로필을 사용합니다.
1. 관리 패널에 로그인합니다.
1. 만들기 *10개 고객 그룹*.
1. 아래 쿼리를 실행하여 제품에 추가 `_cl` 표:

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. 아래 명령을 실행하여 부분 가격 색인화 프로세스를 트리거합니다.

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>예상 결과</u>:

SQL 쿼리 DELETE `main_table` 출처: `catalog_product_index_price` 는 빠르게 실행됩니다.

<u>실제 결과</u>:

SQL 쿼리 DELETE `main_table` 출처: `catalog_product_index_price` 는 매우 느리게 실행됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
