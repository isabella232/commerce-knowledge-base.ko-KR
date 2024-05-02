---
title: "ACSD-55427: 관리자는 **에서 제품 할당을 취소할 수 없습니다.[!UICONTROL Product in Shared Catalogs]**의 페이지에 표시"
description: ACSD-55427 패치를 적용하여 제품에서 할당 해제할 수 없는 Adobe Commerce 문제를 **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427: 관리자는에서 제품 할당을 취소할 수 없습니다. **[!UICONTROL Product in Shared Catalogs]** 제품 페이지에서

ACSD-55427 패치는에서 제품 할당을 취소할 수 없는 문제를 해결합니다 **[!UICONTROL Product in Shared Catalogs]** Commerce 관리자의 카탈로그에 있는 제품 페이지에서 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44가 설치되어 있습니다. 패치 ID는 ACSD-55427입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

에서 제품 할당을 취소할 수 없습니다. **[!UICONTROL Product in Shared Catalogs]** Commerce 관리자의 카탈로그에 있는 제품 페이지에서

<u>재현 단계</u>:

사전 요구 사항: Adobe Commerce이 B2B 및 와 함께 설치됨 **[!UICONTROL Shared Catalogs]** 활성화되었습니다.
1. 제품을 만듭니다.
1. 공유 카탈로그 대시보드로 이동하여 기본 공유 카탈로그를 엽니다.
1. 제품을 기본 카탈로그에 지정하고 제품 가격보다 낮은 가격을 설정합니다.
1. 공유 카탈로그를 저장합니다.
1. 실행 [!UICONTROL CRON] 소비자/인덱서를 업데이트하려면
1. 제품을 열고 아래에서 제품을 제거합니다. **[!UICONTROL Product in Shared Catalogs]** 섹션.

<u>예상 결과</u>:

제품은에서 제거해야 합니다. **[!UICONTROL Product in Shared Catalogs]** 섹션.

<u>실제 결과</u>:

제품이 여전히 **[!UICONTROL Product in Shared Catalogs]** 섹션.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
