---
title: 'ACSD-55305: 에서 회사 사용자를 편집하는 동안 팝업이 중지됨 [!UICONTROL My Account]'
description: 'ACSD-55305 패치를 적용하여 Adobe Commerce 문제 해결 위치: [!UICONTROL Edit Company User] 다음에 팝업 [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] 페이지가 화면에 로더로 고정되어 있습니다.'
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305:에서 회사 사용자를 편집하는 동안 팝업이 중단됨 [!UICONTROL My Account]

ACSD-55305 패치는 다음과 같은 문제를 해결합니다.  [!UICONTROL Edit Company User] 다음에 팝업 [!UICONTROL My Account]> [!UICONTROL Company Structure] 페이지가 화면에 로더로 고정되어 있습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43이 설치되었습니다. 패치 ID는 ACSD-55305입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

을(를) 사용하려고 할 때 오류가 발생합니다. *[!UICONTROL Edit Company User]* 다음에 팝업 *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* 화면에 표시된 로더로 페이지가 고정됩니다.

<u>재현 단계</u>:

1. B2B 회사를 만듭니다.
1. 고객을 위한 다중 선택 속성을 만듭니다.
1. 회사 관리자의 새로 만든 속성에 값을 할당합니다.
1. 회사 관리자로 로그인합니다.
1. 로 이동 [!UICONTROL account dashboard] 다음 위치로 이동 **[!UICONTROL Company Structure]**.
1. 사용자를 선택합니다.
1. 클릭 **[!UICONTROL Edit Selected]**.

<u>예상 결과</u>:

양식 팝업이 정확하게 표시되어 회사 정보를 편집할 수 있는 옵션을 제공합니다.

<u>실제 결과</u>:

양식 팝업은 편집할 수 없는 상태로 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
