---
title: 'ACSD-51036: 동시 REST API 호출 중 경합 조건은 배송 상태를 덮어씁니다.'
description: ACSD-51036 패치를 적용하여 동시 REST API 호출 중에 경합 상태가 발생하여 주문 항목 테이블의 배송 상태를 덮어쓰는 Adobe Commerce 문제를 해결합니다.
exl-id: 12d90de7-fe5c-4fcc-b84a-d420dcd871ca
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-51036: 동시 REST API 호출 중 경합 조건은 주문 품목 테이블의 운송 상태를 덮어씁니다

ACSD-51036 패치는 동시 REST API 호출 중 경합 조건이 주문 품목 테이블의 운송 상태를 덮어쓰는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.31이 설치되었습니다. 패치 ID는 ACSD-51036입니다. 이 문제는 Adobe Commerce 2.4.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

동시 REST API 호출 중 경합 조건은 주문 품목 테이블의 운송 상태를 덮어씁니다.

<u>재현 단계</u>:

1. 두 개의 품목으로 주문을 생성합니다.
1. 송장 품목 A.
1. 품목 B에 대한 출하 요청을 전송하는 동시에 REST API를 통해 품목 A에 대한 환불 요청을 전송합니다.
1. 주문으로 이동 **[!UICONTROL Admin Panel]**.

<u>예상 결과</u>

*[!UICONTROL Shipped 1]* 의 항목 B에 대한 상태가 있어야 합니다. *[!UICONTROL Items]* 테이블을 정렬했습니다.

<u>실제 결과</u>

*[!UICONTROL Shipped 1]* 의 항목 B에 대한 상태가 존재하지 않습니다. *[!UICONTROL Items]* 테이블을 정렬했습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
