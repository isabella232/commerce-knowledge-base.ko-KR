---
title: 'ACSD-56616: 단순 재고 부족 시 번들 제품의 상점 표시'
description: ACSD-56616 패치를 적용하여 관련된 모든 단순 제품의 재고가 없을 때 번들 제품이 상점 앞에 예기치 않게 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: 6cf8e15d-38a5-42b6-aee7-67410b501404
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616: 단순 재고 부족 시 번들 제품의 상점 전광판 표시.

ACSD-56616 패치는 관련된 모든 단순 제품의 재고가 없을 때 번들 제품이 예기치 않게 상점 앞에 표시되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45가 설치되어 있습니다. 패치 ID는 ACSD-56616입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

단순 재고 부족 시 번들 제품의 잘못된 상점 전면 표시.

<u>재현 단계</u>:

1. 새 웹 사이트/스토어/상점을 만듭니다.
1. 새 소스를 만듭니다.
1. 새 스톡을 생성하고 새로 생성된 웹 사이트에 지정합니다.
1. 인덱서가 일정에 따라 업데이트되도록 구성합니다.
1. S1(수량 = 1)과 S2(수량 = 1), 이렇게 두 개의 간단한 제품을 생성하여 신규 주식과 신규 웹 사이트에 지정합니다.
1. 만들기 *번들1* 제품을 새 웹 사이트와 연결하여 카테고리에 배치 *고양이*.
1. 두 개의 필수 드롭다운 옵션 정의 및 단순 제품 연결 *S1* 옵션1 및 *S2* option2에 추가합니다.
1. 제품을 저장합니다.
1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** 및 활성화 *URL에 스토어 코드 추가* = *예*.
1. 상점을 열고 번들 제품을 구입합니다.
1. 크론을 두 번 실행하세요.
1. (으)로 돌아가기 *고양이* 범주.

<u>예상 결과</u>:

다음 *bundle1* 제품이 품절되었습니다.

<u>실제 결과</u>:

다음 *bundle1* 제품이 가격=과 함께 표시됨 *US$0*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
