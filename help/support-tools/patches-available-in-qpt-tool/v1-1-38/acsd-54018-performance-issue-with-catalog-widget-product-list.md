---
title: 'ACSD-54018: 카탈로그 위젯 제품 목록의 성능 문제'
description: ACSD-54018 패치를 적용하여 조건 및 속성 유형 부울이 있는 카탈로그 위젯 제품 목록을 추가할 때 페이지가 느리게 로드되는 Adobe Commerce 문제를 해결합니다.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 9f20484d-58c7-49d8-87df-1eeb84bee6fe
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-54018: 카탈로그 위젯 제품 목록의 성능 문제

ACSD-54018 패치는 조건 및 속성 유형 부울이 있는 카탈로그 위젯 제품 목록을 추가할 때 페이지가 느리게 로드되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38이 설치되었습니다. 패치 ID는 ACSD-54018입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

조건 및 속성 유형 부울이 있는 카탈로그 위젯 제품 목록을 추가할 때 페이지가 느리게 로드됩니다.

<u>재현 단계</u>:

1. 100k 제품을 생성합니다.
1. 범위가 로 설정된 부울 속성 생성 [!UICONTROL Store View].
1. 모든 속성 집합에 속성을 지정합니다.
   * 속성 값 할당 *예* 모든 제품에 적용.
1. 이제 다음으로 이동 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;를 클릭하고 10만 개의 제품을 모두 선택합니다.
   * 선택 **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * bool 속성을 다음으로 설정 *예* 구해
   * 이 단계에서 로그아웃한 경우 다음을 확인하십시오. *메모*.
1. CLI로 이동한 후 실행 `php bin/magento queue:con:start product_action_attribute.update`.
   * 모든 제품의 특성이 업데이트되었는지 확인하십시오.
1. 이제 다음으로 이동 **[!UICONTROL Content]** > **[!UICONTROL Pages]** 새 페이지를 만듭니다.
1. 열기 **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. 선택 *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. 조건 설정 *[!UICONTROL Created attribute]* 끝 *[!UICONTROL Yes]* 구해
1. 프론트엔드로 이동하여 만든 페이지를 엽니다.
1. 전체 페이지 캐시를 비활성화하고 HTML 캐시를 차단합니다.
1. 페이지 로드 속도를 확인합니다.
1. 페이지를 몇 번 다시 로드하고 평균 로드 시간을 계산합니다.

<u>예상 결과</u>:

페이지가 빠르게 로드됩니다.

<u>실제 결과</u>:

페이지를 로드하는 데 5~10초 정도 소요됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
