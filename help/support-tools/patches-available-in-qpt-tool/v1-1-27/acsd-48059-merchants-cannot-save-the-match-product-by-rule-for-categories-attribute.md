---
title: '''ACSD-48059: 판매자가 저장할 수 없음 [!UICONTROL Match product by rule] 카테고리 속성을 사용합니다.'
description: ACSD-48059 패치를 적용하여 판매자가 를 저장할 수 없는 Adobe Commerce 문제를 해결합니다. [!UICONTROL Match product by rule] Categories 속성의 경우
exl-id: 97213157-1b54-4634-9c76-c9ab8fa96e17
feature: Admin Workspace, Attributes, Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-48059: 판매자가 *[!UICONTROL Match product by rule]* categories 속성의 경우

ACSD-48059 패치는 판매자가 을 저장할 수 없는 문제를 해결합니다. *[!UICONTROL Match product by rule]* 의 categories 속성에 대해 [!DNL Visual Merchandiser]. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치되었습니다. 패치 ID는 ACSD-48059입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) >=2.3.7 &lt;2.4.7

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

판매자가 다음을 저장할 수 없음 *[!UICONTROL Match product by rule]* 의 categories 속성에 대해 [!DNL Visual Merchandiser].

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Visual Merchandiser]** > **[!UICONTROL Visible Attributes for Category Rules]**, 카테고리를 추가합니다.
1. Adobe Commerce 관리자로 이동 > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
   * 로 이동 [!UICONTROL Products in Category] 섹션.
   * 새 항목 추가 *[!UICONTROL Match products by rule]* categories 속성이 있는 조건.

<u>예상 결과</u>:

범주가 저장되었습니다.

<u>실제 결과</u>:

* 새 규칙 및 조건으로 범주를 저장할 수 없습니다.
* *범주를 저장하는 동안 문제가 발생했습니다.* 오류가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
