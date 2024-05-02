---
title: '''ACSD-48634: [!DNL JS] 다음과 같은 경우 오류 발생 [!DNL Google Analytics Content Experiments] 활성화됨'
description: ACSD-48634 패치 적용 [!DNL JS] 오류 [!DNL staging] 다음과 같은 경우 페이지 업데이트 [!DNL Google Analytics Content Experiments] 이(가) 활성화되었습니다.
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] 다음과 같은 경우 오류 발생 [!DNL Google Analytics Content Experiments] 활성화됨

ACSD-48634 패치 수정 사항 [!DNL JS] 오류 [!DNL staging] 다음과 같은 경우 페이지 업데이트 [!DNL Google Analytics Content Experiments] 이(가) 활성화되었습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치되었습니다. 패치 ID는 ACSD-48634입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL JS] 오류가 다음에서 발생합니다. [!DNL staging] 다음과 같은 경우 페이지 업데이트 [!DNL Google Analytics Content Experiments] 이(가) 활성화되었습니다.

<u>재현 단계</u>:

1. 위치 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, 추가 웹 사이트 만들기, 저장 및 **[!UICONTROL Store View]**. 다음을 확인합니다. **[!UICONTROL Store View]** 은(는) *[!UICONTROL Enabled]*.
1. 구성 **[!DNL Configure Google Analytics]** 로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * 대상 **[!DNL Main]** 및 추가 웹 사이트 [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* 다른 필드의 경우, 단, 변경하지 마십시오.
   * 대상 **[!DNL Default Config]** [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. 사용 안 함 **[!DNL Configure Google Analytics]** 날짜 **[!DNL Default Config]** [!DNL scope] 변경하여 **[!UICONTROL Enable]** 출처: *[!UICONTROL Yes]* 끝 *[!UICONTROL No]*. 다른 것은 변경하지 않도록 주의하십시오!
1. 다음으로 이동 **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. 만들기 및 편집 **[!UICONTROL category]** 예약된 업데이트를 추가합니다.
   * 모든 이름, 미래의 시작 날짜, 미래의 종료 날짜 및 **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. 업데이트를 저장하고 다음을 확인합니다. [!DNL browser developer console] 오류.

<u>예상 결과</u>:

아니요 [!DNL JS] 오류 및 변경 사항 [!DNL staging] 업데이트가 저장되었습니다.

<u>실제 결과</u>:

[!DNL JS] 콘솔에 오류가 표시되고 양식의 형식이 잘못되었으며 [!DNL spinner] 저장 후 비활성화되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
