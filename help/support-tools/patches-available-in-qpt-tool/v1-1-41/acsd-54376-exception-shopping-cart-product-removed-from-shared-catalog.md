---
title: 'ACSD-54376: 제품이에서 제거된 경우 장바구니에 예외 [!UICONTROL shared catalog]'
description: ACSD-54376 패치를 적용하여 제품이 장바구니에서 제거될 때 장바구니에서 예외가 발생하는 Adobe Commerce 문제를 수정합니다 [!UICONTROL shared catalog] 장바구니에 추가된 후.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: a1e5c084-532f-49e8-ab87-6674b44218e8
source-git-commit: 1cc565d5888e5a380c04879d9aced2c19e92c2e5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54376: 제품이에서 제거된 경우 장바구니에 예외 [!UICONTROL shared catalog]

ACSD-54376 패치는 제품이에서 제거될 때 장바구니에서 예외가 발생하는 문제를 수정합니다 [!UICONTROL shared catalog] 장바구니에 추가된 후. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41이 설치되었습니다. 패치 ID는 ACSD-54376입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니에서 제품을 제거할 때 예외가 발생합니다. [!UICONTROL shared catalog] 장바구니에 추가된 후.

<u>재현 단계</u>:

1. B2B와 함께 Adobe Commerce을 설치합니다.
1. 사용 [!UICONTROL shared catalog].
1. 제품을 만들고 기본값에 할당 [!UICONTROL shared catalog].
1. 상점 첫 화면에서 장바구니에 제품을 추가합니다.
1. 에서 제품 제거 [!UICONTROL shared catalog].
1. 미니 장바구니 드롭다운을 사용하여 체크아웃 페이지로 이동합니다.

<u>예상 결과</u>:

예외는 처리되며 사용자에게 표시되지 않습니다.

<u>실제 결과</u>:

처리되지 않은 예외가 체크아웃 페이지에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
