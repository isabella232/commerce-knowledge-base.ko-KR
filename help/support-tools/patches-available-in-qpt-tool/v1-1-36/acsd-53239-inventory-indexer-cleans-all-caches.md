---
title: 'ACSD-53239: 인벤토리 인덱서가 모든 캐시를 정리합니다.'
description: ACSD-53239 패치를 적용하여 인벤토리 인덱서가 의 모든 캐시를 정리하는 Adobe Commerce 문제를 해결합니다. [!UICONTROL Update on Schedule] 모드.
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
exl-id: b8e68cf7-d326-4c9e-8749-d83113de2070
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-53239: 인벤토리 인덱서가 의 모든 캐시를 정리합니다. [!UICONTROL Update on Schedule] 모드

ACSD-53239 패치는 인벤토리 인덱서가 의 모든 캐시를 정리하는 문제를 해결합니다 [!UICONTROL Update on Schedule] 모드. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36이 설치되었습니다. 패치 ID는 ACSD-53239입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

인벤토리 인덱서가 의 모든 캐시를 정리합니다. [!UICONTROL Update on Schedule] 모드.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]** 및 정보 선택 *1200* 제품.
2. 업데이트 *[!UICONTROL Qty]* 새 값에 추가 및 클릭 **[!UICONTROL Save]**.
3. 실행 `bin/magento cron:run` 저장 후 즉시.
4. 다음 GraphQL 쿼리를 실행합니다.

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>예상 결과</u>

쿼리는 일반적인 시간 내에 처리됩니다.

<u>실제 결과</u>

쿼리가 비정상적으로 느리게 처리됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
