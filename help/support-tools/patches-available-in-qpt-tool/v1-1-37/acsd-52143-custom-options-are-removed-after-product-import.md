---
title: 'ACSD-52143: 사용자 지정 옵션은 제품 가져오기 후 제거됨'
description: ACSD-52143 패치를 적용하여 제품 가져오기 후 사용자 지정 옵션이 제거되는 Adobe Commerce 문제를 해결합니다.
feature: Data Import/Export
role: Admin, Developer
exl-id: 7dde1efe-37a3-443f-9ce1-82cf1b3d9da7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-52143: 사용자 지정 옵션은 제품 가져오기 후 제거됩니다

ACSD-52143 패치는 제품 가져오기 후 사용자 지정 옵션이 제거되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37이 설치되었습니다. 패치 ID는 ACSD-52143입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자 지정 옵션은 제품을 가져온 후 제거됩니다.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Store]** > **[!UICONTROL All Stores]**&#x200B;을 클릭하고 다중 스토어 인스턴스(스토어 보기가 두 개인 웹 사이트 한 개)를 설정합니다.
1. 다음으로 이동 **[!UICONTROL Catalog]** > **[!UICONTROL Products]** 및 을 사용하여 두 개의 제품 만들기 [!UICONTROL Customizable Options].
1. 각 제품에서 [!UICONTROL Customizable Option].
1. 두 번째 스토어 보기로 전환하고 각 제품의 제품 이름을 수정합니다.
1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** 만든 두 제품을 내보냅니다.
1. CSV 파일을 다운로드합니다.
1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** 파일을 다시 가져옵니다.
1. 두 제품을 모두 확인합니다.

<u>예상 결과</u>:

사용자 지정 옵션은 제품을 가져온 후에는 제거되지 않습니다.

<u>실제 결과</u>:

세관 옵션은 제품을 수입한 후에 제거됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
