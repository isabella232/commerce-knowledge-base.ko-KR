---
title: 'ACSD-49013: 이메일 확인이 웹 사이트 로케일로 번역되지 않음'
description: ACSD-49013 패치를 적용하여 벌크 API를 사용하여 고객을 만들 때 이메일 확인이 웹 사이트 로케일로 번역되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 68203bd4-021a-4736-a793-4b6663a9c66b
feature: Admin Workspace, Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49013: 이메일 확인이 웹 사이트 로케일로 번역되지 않음

ACSD-49013 패치는 벌크 API를 사용하여 고객을 만들 때 이메일 확인이 웹 사이트 로케일로 번역되지 않는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치되었습니다. 패치 ID는 ACSD-49013입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

벌크 API를 사용하여 고객을 만들 때 이메일 확인이 웹 사이트 로케일로 번역되지 않습니다.

<u>재현 단계</u>:

1. 다음과 같은 다른 로케일 설치 `de_DE`.
1. 구성 *RabbitMQ*.
1. 실행 `bin/magento setup:upgrade` RabbitMQ에 큐를 설치하고 언어 팩을 설정합니다.
1. 에서 추가 웹 사이트 만들기 [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. 이 새 웹 사이트의 로케일을 다음으로 설정 `de_DE` 위치: [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**.
1. API 호출을 실행하여 일괄 API를 사용하여 고객 계정을 생성합니다. 해당 항목 사용 `website_id`.

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. 실행 `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`.
1. 지정된 웹 사이트에서 고객 계정이 올바르게 생성되었는지 확인할 수 있습니다.
1. 고객 등록을 위해 받은 이메일을 확인합니다.

<u>예상 결과</u>:

고객이 지정된 웹 사이트에서 생성되기 때문에 등록 이메일은 해당 웹 사이트의 로케일을 사용하여 전송됩니다.

<u>실제 결과</u>:

고객은 지정된 웹 사이트에서 올바르게 생성되지만, 벌크 API를 사용하는 경우 기본 로케일을 사용하여 등록 이메일이 전송됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
