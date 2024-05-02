---
title: 'ACSD-47497: 스토어 / 구성 / 서비스에 대한 ACL 누락 [!UICONTROL OAuth]'
description: ACSD-47497 패치를 적용하여 특정 역할에 대한 권한이 설정되어 구성 섹션에 대한 액세스를 정의할 수 없는 경우 Adobe Commerce 문제를 해결합니다.
exl-id: c13fd541-1379-4893-9190-9da1422b2b99
feature: Configuration, Identity Management, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-47497: 스토어 / 구성 / 서비스에 대한 ACL 누락 [!UICONTROL OAuth]

ACSD-47497 패치는 다음과 같은 문제를 해결합니다. **[!UICONTROL Services]** 에 탭이 표시되지 않음 **[!UICONTROL Configuration]** Adobe Commerce 섹션에 있는 마지막 항목이 될 필요가 없습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23이 설치되었습니다. 패치 ID는 ACSD-47497입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**
* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

특정 역할에 대한 권한을 설정하면 액세스 권한을 정의할 수 없습니다 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**.

<u>재현 단계</u>:

1. Adobe Commerce 관리자에 로그인합니다. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. 선택 **[!UICONTROL Role Resources]** 관리자 역할에서 다음을 설정합니다. **[!UICONTROL Resource Access]** 아래에 **[!UICONTROL Roles Resources]** 끝 _사용자 정의_&#x200B;를 클릭한 다음 모든 확인란을 선택합니다. 선택 **[!UICONTROL Save Role]**.
1. 선택 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]**. 다음 **[!UICONTROL OAuth]** 구성 섹션을 사용할 수 없습니다.

<u>예상 결과</u>:

위치 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**&#x200B;구성 섹션이 표시됩니다.

<u>실제 결과</u>:

위치 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**, 구성 섹션이 누락되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
