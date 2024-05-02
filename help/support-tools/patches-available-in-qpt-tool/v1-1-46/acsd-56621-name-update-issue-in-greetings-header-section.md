---
title: 'ACSD-56621: 회사 관리자의 인사말 헤더에 업데이트된 이름이 표시되지 않음'
description: ACSD-56621 패치를 적용하여 회사 관리자 사용자의 업데이트된 이름과 성이 인사말 헤더 섹션에 반영되지 않은 Adobe Commerce 문제를 수정합니다.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 4ad9c878-b617-4e6a-939c-be15faf7124b
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56621: 회사 관리자의 인사말 헤더에 업데이트된 이름이 표시되지 않음

ACSD-56621 패치는 회사 관리자 사용자의 업데이트된 이름과 성이 인사말 헤더 섹션에 반영되지 않는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46이 설치되었습니다. 패치 ID는 ACSD-56621입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

업데이트된 이름은 회사 관리자의 인사말 헤더에 표시되지 않습니다.

<u>재현 단계</u>:

1. 다음 위치로 이동 **[!UICONTROL Admin]** 패널.
1. 다음으로 이동 **[!UICONTROL Stores]** 및 선택 **[!UICONTROL Configuration]**.
1. 아래 **[!UICONTROL General]** 섹션, 선택 **[!UICONTROL B2B]** 을 클릭하여 B2B 회사 기능을 활성화합니다.
1. 로 이동 **[!UICONTROL Storefront]** 새 회사를 등록합니다.
1. 회사 관리자로 로그인합니다.
1. 다음으로 이동 **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** 필요에 따라 이름 및 성 필드를 수정합니다.

<u>예상 결과</u>:

인사말 헤더 섹션의 사용자 이름과 성이 즉시 변경됩니다.

<u>실제 결과</u>:

사용자의 이름과 성은 사용자가 로그아웃했다가 다시 로그인할 때만 변경됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
