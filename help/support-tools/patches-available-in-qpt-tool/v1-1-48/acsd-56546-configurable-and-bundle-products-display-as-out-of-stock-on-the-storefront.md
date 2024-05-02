---
title: 'ACSD-56546: 구성 및 번들 제품이 상점 앞에 품절로 표시됨'
description: ACSD-56546 패치를 적용하여 *일 때 구성 가능한 및 번들 제품이 상점 첫 화면에서 품절로 표시되는 Adobe Commerce 문제를 해결합니다.[!UICONTROL Display Out of Stock Products]* 구성 옵션이 비활성화되었습니다.
feature: Storefront, Products
role: Admin, Developer
exl-id: 488e2c69-442f-45e1-aa8f-71d9c0a93950
source-git-commit: 031d5cad6727bac61c88f21fa7c84e0d2a6df331
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546: 구성 및 번들 제품이 상점 앞에 품절로 표시됨

ACSD-56546 패치는 구성 가능 및 번들 제품이 상점 첫 화면에서 품절로 표시되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48이 설치되었습니다. 패치 ID는 ACSD-56546입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음과 같은 경우 구성 및 번들 제품이 재고가 없는 상태로 상점 앞에 표시됨 *[!UICONTROL Display Out of Stock Products]* 옵션이 비활성화되었습니다.

<u>재현 단계</u>:

1. 설정 **[!UICONTROL Display Out of Stock Products]** 옵션 대상 *아니요*.
1. 웹 사이트, 스토어 및 스토어를 만듭니다.
1. 소스 및 스톡을 만든 다음 두 번째 웹 사이트에 할당합니다.
1. 만들기 *구성 가능한 제품* 두 가지 하위 제품이 있습니다. 하위 제품을 소스와 웹 사이트 모두에 할당합니다.
1. 첫 번째 하위 제품을으로 업데이트 *qty=0* 두 소스 모두에서.
1. 두 번째 하위 제품을 업데이트하고 두 번째 웹 사이트에서 비활성화합니다.
1. 전체 색인 재지정을 수행합니다.
1. 두 번째 웹 사이트에서 구성 가능한 제품이 포함된 카테고리를 확인하십시오.

<u>예상 결과</u>:

품절 구성 가능 제품은 상점 앞에 표시되지 않습니다.

<u>실제 결과</u>:

다음과 같은 경우에도 품절 구성 가능한 제품이 상점 앞에 표시됩니다. *[!UICONTROL Display Out of Stock Products]* 옵션이 비활성화되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
