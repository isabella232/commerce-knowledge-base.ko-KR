---
title: 'ACSD-49392: 부분 환불 후 주문 상태가 마감으로 변경됨'
description: ACSD-49392 패치를 적용하여 번들 제품에 대한 부분 환불 후 주문 상태가 종료됨으로 변경되는 Adobe Commerce 문제를 수정합니다.
exl-id: fca6f502-e224-4444-b0d0-f823853c9458
feature: Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-49392: 부분 환불 후 주문 상태가 마감으로 변경됨

ACSD-49392 패치는 번들 제품에 대한 부분 환불 후 주문 상태가 종료됨으로 변경되는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.31이 설치되었습니다. 패치 ID는 ACSD-49392입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.3.7-p4 및 2.4.1 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

묶음 제품에 대한 부분 환불 후 주문 상태가 마감으로 변경됩니다.

<u>재현 단계</u>:

1. Adobe Commerce에 로그인하고 모든 번들 제품을 만들거나 기존 번들 제품을 사용합니다.
1. 수량이 1보다 큰 이 묶음 상품을 주문하세요.
1. 관리자로 이동하여 2단계에서 만든 주문을 엽니다. **[!UICONTROL Sales]** > **[!UICONTROL Order]** 송장을 생성합니다. 주문 상태를 확인합니다. 처리 중입니다.
1. 부분 대변 메모를 생성합니다(번들의 모든 제품에 대해 환불 안 함).
1. 주문 상태를 확인합니다.

<u>예상 결과</u>

묶음 상품에 대한 부분 대변 메모를 작성한 후, 주문 상태는 처리 중입니다.

<u>실제 결과</u>

묶음 제품에 대한 부분 대변 메모를 작성한 후 주문 상태는 완료입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
