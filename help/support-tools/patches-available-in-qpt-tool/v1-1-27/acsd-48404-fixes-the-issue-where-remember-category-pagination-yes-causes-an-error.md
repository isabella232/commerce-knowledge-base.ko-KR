---
title: "ACSD-48404: *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* 브라우저의 뒤로 단추를 누를 때 오류가 발생합니다."
description: ACSD-48404 패치를 적용하여 다음과 같은 Adobe Commerce 문제를 해결합니다. *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* 브라우저의 뒤로 단추를 누르면 오류가 발생합니다.
exl-id: b4b96198-dee6-4b3c-b60a-0983ef8ef7b2
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-48404: *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* 브라우저의 뒤로 단추를 누르면 오류 발생

ACSD-48404 패치는 다음과 같은 문제를 해결합니다. *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* 브라우저의 뒤로 단추를 누르면 오류가 발생합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치되었습니다. 패치 ID는 ACSD-48404입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* 브라우저의 뒤로 단추를 누르면 오류가 발생합니다.


<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]**, 및 설정 *[!UICONTROL Remember Category Pagination]* 끝 *예*.
1. 상점 앞에서 카테고리를 엽니다.
1. 에서 기본값이 아닌 값을 선택합니다. *[!UICONTROL Show Per Page]* 드롭다운입니다. 옵션을 선택하면 페이지가 다시 로드됩니다.
1. 페이지가 다시 로드되면 카탈로그 페이지에서 제품을 클릭합니다.
1. 열려 있는 제품 세부 사항 페이지에서 **[!UICONTROL Back]** 브라우저의 단추입니다.

<u>예상 결과</u>:

카탈로그 페이지가 다시 열립니다.

<u>실제 결과</u>:

카테고리 페이지가 오류를 반환합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
