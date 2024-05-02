---
title: 'ACSD-54324: GraphQL requisition_lists 요청은 페이지 매김 설정을 고려하지 않습니다.'
description: ACSD-54324 패치를 적용하여 GraphQL 'requisition_lists' 요청이 페이지 매김 설정을 고려하지 않고 모든 결과를 반환하는 Adobe Commerce 문제를 해결합니다.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324: GraphQL `requisition_lists` 요청이 페이지 매김 설정을 고려하지 않음

ACSD-54324 패치를 사용하면 GraphQL에서 발생하는 문제가 해결됩니다 `requisition_lists` 요청은 페이지 매김 설정을 고려하지 않고 모든 결과를 반환합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.41이 설치되었습니다. 패치 ID는 ACSD-54324입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

더 GraphQL `requisition_lists` 요청은 페이지 매김 설정을 고려하지 않고 모든 결과를 반환합니다.

<u>재현 단계</u>:

1. Admin에 로그인하고 다음으로 이동합니다. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * 설정 *[!UICONTROL Enable Requisition List]* 끝 *예*.

1. 프론트엔드에 로그인하고 **[!UICONTROL My Requisition Lists]** 상단 메뉴 또는 **[!UICONTROL My Account]**&#x200B;을 누르고 여러 구매요청을 생성합니다(예: 7).
1. 고객 토큰을 생성한 후 아래 GraphQL을 실행합니다 `requisition_lists` 고객을 질의합니다.

   * 페이지 크기가 사용자가 생성한 총 구매요청 목록 수보다 작은지 확인합니다(예: 4).

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. 의 값이 `total_count` 필드에 7이 표시되며, 이때 4가 표시됩니다.

   항목 수가 와 동일해야 하는 경우 7개도 표시됩니다. *페이지 크기*.

<u>예상 결과</u>:

* 다음으로 나열된 번호 *페이지 크기* 다음에 반환됨 `total_count` 총 레코드 수가 아닙니다.
* 항목 수는 와(과) 같습니다. *페이지 크기*.

<u>실제 결과</u>:

아래에 반환되는 총 레코드 수 `total_count`, 비록 *페이지 크기* 이(가) 언급되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
