---
title: 'ACSD-46865: [!UICONTROL shipment] 및 [!UICONTROL credit memo] 다음과 같은 경우 채워지지 않음 [!UICONTROL asynchronous indexing] 활성화됨'
description: 'ACSD-46865 패치를 적용하여 Adobe Commerce 문제 해결 위치: [!UICONTROL shipment] 및 [!UICONTROL credit memo] 다음 경우에는 그리드가 채워지지 않습니다. [!UICONTROL asynchronous indexing] 이(가) 활성화되었습니다.'
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] 및 [!UICONTROL credit memo] 다음과 같은 경우 채워지지 않음 [!UICONTROL asynchronous indexing] 활성화됨

ACSD-46865 패치는 다음과 같은 문제를 해결합니다. [!UICONTROL shipment] 및 [!UICONTROL credit memo] 다음 경우에는 그리드가 채워지지 않습니다. [!UICONTROL asynchronous indexing] 이(가) 활성화되었습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되었습니다. 패치 ID는 ACSD-46865입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Shipment] 및 [!UICONTROL credit memo] 다음 경우에는 그리드가 채워지지 않습니다. [!UICONTROL asynchronous indexing] 이(가) 활성화되었습니다.

<u>재현 단계</u>:

1. 다음에서 [!DNL Commerce] 책임자, 다음으로 이동 **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *예*.
2. 다시 다음으로 이동 **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. 구성 캐시를 정리합니다.
4. 간단한 제품에 대해 새로운 손님 주문을 합니다.
5. 크론 실행
6. 에서 주문을 엽니다. [!UICONTROL Commerce] 로 이동하여 관리자 **[!UICONTROL Sales]** > **[!UICONTROL Orders]** 송장 및 대변 메모를 생성합니다.
7. 주문을 다음으로 이동 [!UICONTROL Archive].
8. 간단한 제품에 대해 다른 주문을 만듭니다.
9. 크론 실행
10. 신규 주문으로 이동하여 신규 선적, 송장 및 대변 메모를 생성합니다.
11. 크론 실행
12. 다음 확인: [!UICONTROL shipments], [!UICONTROL invoices], 및 [!UICONTROL credit memo] 관리자의 그리드.

<u>예상 결과</u>:

신규 [!UICONTROL shipment], [!UICONTROL invoice] 및 [!UICONTROL credit memo] 표시됩니다.

<u>실제 결과</u>:

신규 [!UICONTROL shipment], [!UICONTROL invoice], 및 [!UICONTROL credit memo] 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
