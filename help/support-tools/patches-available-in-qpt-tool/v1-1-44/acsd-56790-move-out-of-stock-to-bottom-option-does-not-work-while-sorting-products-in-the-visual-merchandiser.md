---
title: 'ACSD-56790: **[!UICONTROL move out of stock to bottom]에서 제품을 정렬하는 동안 ** 옵션이 작동하지 않습니다.  [!DNL Visual Merchandiser]'
description: ACSD-56790 패치를 적용하여 Visual Merchandiser에서 제품을 정렬하는 동안 재고 부족 상태에서 하단으로 이동 옵션이 작동하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# ACSD-56790: **[!UICONTROL move out of stock to bottom]** 에서 제품을 정렬하는 동안 옵션이 작동하지 않음 [!DNL Visual Merchandiser]

ACSD-56790 패치는에서 제품을 정렬하는 동안 재고 부족 상태에서 하단으로 이동 옵션이 작동하지 않는 문제를 해결합니다. [!DNL Visual Merchandiser]. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44가 설치되어 있습니다. 패치 ID는 ACSD-56790입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음 **[!UICONTROL move out of stock to bottom]** 에서 제품을 정렬하는 동안 옵션이 작동하지 않음 [!DNL Visual Merchandiser]

<u>재현 단계</u>:

1. Adobe Commerce을 설치합니다.
1. 다음으로 이동 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** 을 누르고 다음 속성을 만듭니다.
1. 새 웹 사이트 만들기: **기본 아님**.
1. 만들기 **비기본 저장소** 이 새 웹 사이트에서.
1. 두 개의 스토어를 만듭니다.

   * 의 첫 번째 **기본 웹 사이트 스토어**.
   * 에서 두 번째 **비기본 저장소**.

1. 두 개의 소스를 만듭니다.
   * 편지.
   * 숫자.

1. 두 개의 주식을 만듭니다.
   * 첫 번째 주요 - 판매 채널: 주요 웹 사이트 - 지정된 소스: 편지.
   * 두 번째 비주 - 판매 채널: 비주 - 지정된 출처: 숫자.

1. 두 웹 사이트에서 모두 기본값 카테고리의 세 가지 간단한 제품을 만들고 모두 두 소스에 할당합니다.

   * ProductA - 수량 *10* 편지, 수량 *0* 숫자로 표시합니다.
   * 제품1 - 수량 *0* 편지, 수량 *10* 숫자로 표시합니다.
   * ProductA1 - 수량 *10* 편지, 수량 *10* 숫자로 표시합니다.

1. 다음으로 이동 **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** 및 선택  **[!UICONTROL Default category]**.
1. 범위를 다음으로 변경 **첫 번째**.
1. 카테고리 섹션의 제품을 확장합니다.
1. 다음과 같이 정렬 순서를 선택합니다. **[!UICONTROL move out of stock to bottom]**

<u>예상 결과</u>:

이 포함된 제품 목록 **품절** 제품은 맨 아래로 이동됩니다.

<u>실제 결과</u>:

제품 로드에 실패했습니다. 다음 오류 메시지가 표시된 페이지가 관리 대시보드로 리디렉션됩니다. `Invalid security or form key. Please refresh the page`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
