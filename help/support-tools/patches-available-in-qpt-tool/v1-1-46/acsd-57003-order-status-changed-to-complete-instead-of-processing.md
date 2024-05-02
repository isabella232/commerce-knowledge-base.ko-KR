---
title: 'ACSD-57003: *처리 중*으로 변경하는 대신 *완료*로 주문 상태가 변경됨'
description: ACSD-57003 패치를 적용하여 주문 상태가 *처리 중*으로 변경되는 대신 *완료*로 변경되는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: c3c59185-c447-46fa-b404-6c4a4a300315
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-57003: 주문 상태가 다음으로 변경됨 *완료* 을 로 변경하지 않고 *처리 중*

ACSD-57003 패치를 사용하면 주문 상태가 로 변경되는 문제가 해결됩니다. *완료* 을 로 변경하지 않고 *처리 중*. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.46이 설치되었습니다. 패치 ID는 ACSD-57003입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문 상태가 다음으로 변경됨 *완료* 을 로 변경하지 않고 *처리 중* 주문이 일부 환불 및 일부 배송된 경우.

<u>재현 단계</u>:

1. 구성 가능한 두 제품을 사용하여 주문을 만듭니다.
1. 모든 항목에 대한 송장을 발행합니다.
1. 첫 번째 품목만 출하합니다.
1. 출하된 품목에 대해서만 대변 메모 환불/생성(*첫 번째 항목*).
1. 주문 상태를 확인합니다.

<u>예상 결과</u>:

주문 상태는 다음과 같아야 합니다. _처리 중_ 주.

<u>실제 결과</u>:

주문 상태 변경 대상 *완료* 부분 출하된 품목에 대한 대변 메모를 생성한 후

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
