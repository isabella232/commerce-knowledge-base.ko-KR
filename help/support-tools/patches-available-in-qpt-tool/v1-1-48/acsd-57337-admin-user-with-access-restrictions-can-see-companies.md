---
title: "ACSD-57337: 액세스 제한이 있는 관리 사용자는 *회사* 그리드에서 모든 회사를 볼 수 있습니다."
description: 특정 웹 사이트에 대한 액세스 제한이 있는 관리자가 *회사* 그리드의 모든 웹 사이트에서 회사를 볼 수 있는 Adobe Commerce 문제를 해결하려면 ACSD-57337 패치를 적용합니다.
feature: Companies, B2B, Configuration
role: Admin, Developer
source-git-commit: a02c80006f1c8a434fe17322f0c6cee25f086396
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-57337: 액세스 제한이 있는 관리 사용자는 *회사* 격자

ACSD-57337 패치는 특정 웹 사이트에 대한 액세스 제한이 있는 관리자가 의 모든 웹 사이트에서 회사를 볼 수 있는 문제를 수정합니다 *회사* 그리드. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48이 설치되었습니다. 패치 ID는 ACSD-57337입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

특정 웹 사이트에 대한 액세스 제한이 있는 관리자는 의 모든 웹 사이트에서 회사를 볼 수 있습니다 *회사* 그리드.

<u>재현 단계</u>:

1. 추가 웹 사이트, 스토어 및 스토어를 만듭니다.
1. 다른 웹 사이트에 할당된 몇 개의 회사를 만듭니다.
1. 관리자 사용자 역할을 만들고 역할 범위를 만든 웹 사이트로 설정합니다.
1. 관리자를 만들고 만든 역할에 할당합니다.
1. 새 관리자로 로그인합니다.
1. 열기 **[!UICONTROL Customers]** > **[!UICONTROL Companies]** 그리고 회사 목록을 살펴보세요.

<u>예상 결과</u>:

추가 웹 사이트에 할당된 회사는 *회사* 그리드.

<u>실제 결과</u>:

모든 회사가 *회사* 그리드.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.