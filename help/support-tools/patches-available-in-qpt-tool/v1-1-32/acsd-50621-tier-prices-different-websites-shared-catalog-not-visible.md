---
title: 'ACSD-50621: 공유 카탈로그의 여러 웹 사이트에 대한 계층 가격이 표시되지 않음'
description: ACSD-50621 패치를 적용하여 다중 웹 사이트 환경에서 편집할 때 공유 카탈로그의 여러 웹 사이트에 대한 계층 가격이 표시되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 6d6635bc-4f76-4e2f-9bc7-0276cced8ca9
feature: Catalog Management, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-50621: 공유 카탈로그의 여러 웹 사이트에 대한 계층 가격은 표시되지 않습니다

ACSD-50621 패치는 다중 웹 사이트 환경에서 편집할 때 공유 카탈로그의 여러 웹 사이트에 대한 계층 가격이 표시되지 않는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.32가 설치되어 있습니다. 패치 ID는 ACSD-50621입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

공유 카탈로그의 여러 웹 사이트에 대한 계층 가격은 다중 웹 사이트 환경에서 편집할 때 표시되지 않습니다.

<u>재현 단계</u>:

1. 설정 **[!UICONTROL Catalog Price Scope]** 끝 **[!UICONTROL Website]**.
1. 추가 웹 사이트, 스토어 및 스토어를 만듭니다.
1. 간단한 제품을 만들어 모든 웹 사이트에 할당합니다.
1. 사용자 지정 공유 카탈로그를 만듭니다.
1. 다음으로 이동 **[!UICONTROL Set Pricing and Structure]** 사용자 지정 공유 카탈로그에 대해 을 참조하십시오.
1. 1단계: 카탈로그에 대한 제품을 선택합니다. 만든 간단한 제품을 추가합니다.
1. 2단계: 사용자 정의 가격을 설정하고 **[!UICONTROL Configure]**.
1. 웹 사이트마다 다른 계층 가격을 설정합니다.
1. 선택 **[!UICONTROL Done]** 및 클릭 **[!UICONTROL Generate Catalog]** 그런 다음 을 클릭합니다. **[!UICONTROL Save]**.
1. 크론 실행
1. 다음으로 이동 **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** 계층 가격을 확인합니다.

<u>예상 결과</u>:

다른 웹 사이트에 대해 이전에 구성된 모든 계층 가격이 있습니다.

<u>실제 결과</u>:

이전에 구성한 계층 가격이 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
