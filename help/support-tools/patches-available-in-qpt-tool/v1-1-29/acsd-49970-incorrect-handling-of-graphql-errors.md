---
title: 'ACSD-49970: GraphQL 오류를 잘못 처리'
description: 다음과 같은 경우 GraphQL 오류를 잘못 처리하는 Adobe Commerce 문제를 해결하려면 ACSD-49970 패치를 적용합니다. [!UICONTROL New Relic Reporting] 이(가) 켜져 있습니다.
exl-id: 70acade5-02a5-4769-86e2-5c566b2af709
feature: GraphQL, Observability
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49970: GraphQL 오류의 잘못된 처리

ACSD-49970 패치는 다음과 같은 경우 GraphQL 오류를 잘못 처리하는 문제를 해결합니다. *[!UICONTROL New Relic Reporting]* 이(가) 켜져 있습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29가 설치되었습니다. 패치 ID는 ACSD-49970입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`GraphQLOperationNames` 키가 제대로 처리되지 않습니다. `logDataHelper` 이 키를 포함하거나 포함하지 않습니다.

<u>재현 단계</u>:

1. 실행 `bin/magento deploy:mode:set developer`.
1. 관리자에 로그인합니다.
1. 사용 **[!UICONTROL New Relic Integration]** 출처: **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(참고: [!DNL New Relic] 확장을 사용할 수 없으며 구성이 저장됩니다.)
1. 실행 *GraphQL* 다음으로 돌연변이 `http://yourMagentoDomain/graphql` 다음에서 *[!DNL Altair]* 클라이언트 또는 다른 클라이언트 또는 cURL을 통해.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (참고: **[!UICONTROL Header]** 끝 [!UICONTROL Content-Currency:CA] 를 실행하기 전에).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>예상 결과</u>:

없음 *500 예외* 로그에서, `GraphQLOperationNames` 키가 올바르게 처리되고 있습니다.

<u>실제 결과</u>:

다음 항목이 있습니다. *500 예외* 로그에서, `GraphQLOperationNames` 키가 올바르게 처리되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
