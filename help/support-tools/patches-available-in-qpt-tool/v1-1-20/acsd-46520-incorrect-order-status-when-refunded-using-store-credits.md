---
title: 'ACSD-46520: 스토어 크레딧을 사용하여 환불할 때 잘못된 주문 상태'
description: 이 문서에서는 스토어 크레딧을 사용하여 환불할 때 사용자가 잘못된 주문 상태를 얻게 되는 문제에 대한 해결 방법을 제공합니다.
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520: 스토어 크레딧을 사용하여 환불할 때 잘못된 주문 상태

ACSD-46520 패치는 스토어 크레딧을 사용하여 환불할 때 사용자가 잘못된 주문 상태를 받는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20이 설치되었습니다. 패치 ID는 ACSD-46520입니다. 이 문제는 Adobe Commerce 2.4.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3 및 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.5

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

스토어 크레딧을 사용하여 환불할 때 사용자는 잘못된 주문 상태를 받습니다.

<u>재현 단계</u>:

1. 상점 첫 화면에서 고객 계정을 만들고 로그인합니다.
1. 관리자로부터 고객에게 스토어 크레딧을 할당합니다. 매장 크레딧이 전체 주문에 적용되어야 합니다.
1. 스토어 크레딧을 사용하여 주문합니다.
1. 주문에 대한 송장을 발행합니다.
1. 주문의 전체 금액을 환불하기 위해 대변 메모를 생성합니다.
다음 항목 선택 **[!UICONTROL Refund to store credit]** 확인란.
1. 주문 상태를 확인합니다.

<u>예상 결과</u>:

주문 상태는 입니다. *종료됨*.

<u>실제 결과</u>:

주문 상태는 입니다. *완료*&#x200B;은(는) 올바른 상태가 아닙니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 [!DNL Magento Open Source] 온-프레미스: [품질 패치 도구 > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 를 참조하십시오.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 를 참조하십시오.
