---
title: 'ACSD-57854: *GraphQL* 응답에 범주 집계에 나열할 수 없는 비활성화된 범주가 포함됨'
description: ACSD-57854 패치를 적용하여 *GraphQL* 응답에 카테고리 집계에 나열해서는 안 되는 비활성화된 카테고리가 포함된 Adobe Commerce 문제를 해결합니다.
feature: GraphQL
role: Admin, Developer
exl-id: b6130a0f-57bc-4719-99f2-beb630c463c7
source-git-commit: ea6f23a7ce599e24c6b683f82cf08b72b2506020
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57854: *GraphQL* 응답에 범주 집계에 나열되지 않아야 하는 비활성화된 범주가 포함되어 있습니다.

ACSD-57854 패치를 사용하면 다음과 같은 문제가 해결됩니다. *GraphQL* 응답에 범주 집계에 나열할 수 없는 비활성화된 범주가 포함되어 있습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.48이 설치되었습니다. 패치 ID는 ACSD-57854입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*GraphQL* 응답에 범주 집계에 나열할 수 없는 비활성화된 범주가 포함되어 있습니다.

<u>재현 단계</u>:

1. 두 개의 카테고리를 만듭니다.
1. 제품(제품 Adobe 테스트)을 만들고 두 범주 모두에 제품을 할당합니다.
1. 생성된 범주 중 하나를 비활성화합니다.
1. 제품 사용 *GraphQL* 을 클릭하여 제품을 검색합니다.
1. 에서 제품 범주 목록을 확인합니다. *GraphQL* 응답.

<u>예상 결과</u>:

비활성화된 카테고리가 *GraphQL* 응답.

<u>실제 결과</u>:

비활성화된 범주는 범주 집계에 나열됩니다 *GraphQL* 응답.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
