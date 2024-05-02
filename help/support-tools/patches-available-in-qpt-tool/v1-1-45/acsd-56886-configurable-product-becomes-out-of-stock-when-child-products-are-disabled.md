---
title: 'ACSD-56886: 하위 제품이 비활성화되면 구성 가능한 제품이 품절 됨'
description: ACSD-56886 패치를 적용하여 제품이 비활성화될 때 구성 가능한 제품의 재고가 부족해지는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: 809b9829-283f-4e3c-bf27-1944057f944f
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56886: 하위 제품이 비활성화되면 구성 가능한 제품이 품절 상태가 됩니다.

ACSD-56886 패치는 하위 제품이 비활성화될 때 구성 가능한 제품이 품절되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45가 설치되어 있습니다. 패치 ID는 ACSD-56886입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

하위 제품이 비활성화되면 구성 가능한 제품이 품절 상태가 됩니다.

<u>재현 단계</u>:

1. 관리자로 로그인합니다.
1. 의 모든 인덱서 설정 **[!UICONTROL Update By Schedule]** 모드.
1. 다음과 같이 구성 가능한 제품을 만듭니다.

   * 이름 = *테스트 구성 가능 1*
   * 속성 = *색상*
   * 값 = *빨강* 및 *검정*
   * 가격 **빨강**  하위 제품 = *100달러*;
   * &quot;검정색&quot; 하위 제품 가격 = *200달러*.

1. 구성 가능한 제품에 대해 다음과 같은 예정된 업데이트를 만듭니다.

   * 시작일 = *3* 분 후.
   * 종료일 = *5* 시작 날짜로부터 몇 분 후.
   * 제품 이름 = *테스트 구성 가능 1 편집됨*.
   * 비활성화 **빨강** 의 하위 제품 **구성 가능** 섹션.

1. 시작 날짜를 기다립니다.
1. Storefront에서 구성 가능한 제품 세부 사항을 엽니다.

<u>예상 결과</u>:

구성 가능한 제품이 다음과 같이 표시됩니다. **재고 있음** (으)로 **최저 200** 레이블.

<u>실제 결과</u>:

구성 가능한 제품이 다음과 같이 표시됩니다. **품절**.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
