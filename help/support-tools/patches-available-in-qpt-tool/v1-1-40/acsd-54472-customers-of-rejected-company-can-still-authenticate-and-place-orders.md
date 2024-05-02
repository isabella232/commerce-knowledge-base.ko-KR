---
title: 'ACSD-54472: 거부된 회사의 고객은 여전히 인증할 수 있음'
description: ACSD-54472 패치를 적용하여 거부된 회사의 고객이 계속 인증할 수 있고 거부된 및 거부된 회사의 고객이 여전히 주문을 할 수 있는 Adobe Commerce 문제를 수정합니다.
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472: 거부된 회사의 고객은 여전히 인증할 수 있습니다

ACSD-54472 패치는 거부된 회사의 고객이 계속 인증할 수 있고, 차단되고 거부된 회사의 고객이 여전히 주문을 할 수 있는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40이 설치되었습니다. 패치 ID는 ACSD-54472입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

거부된 회사의 고객은 계속 인증할 수 있고, 거부된 및 거부된 회사의 고객은 여전히 주문을 할 수 있습니다.

<u>재현 단계</u>:

1. 회사를 만듭니다.
1. 를 통해 장바구니에 제품 추가 [!DNL GraphQL].
1. 회사 상태를 다음으로 변경 *차단됨*.
1. 보내기 [!DNL GraphQL] 주문 및 협상 가능한 견적 생성을 요청합니다.
1. 회사 상태를 다음으로 변경 *거부됨*.
1. 보내기 [!DNL GraphQL] 회사의 사용자 인증 토큰을 가져오도록 요청합니다.
1. 고객 상태를 다음으로 설정 *비활성*.
1. 보내기 [!DNL GraphQL] 회사의 사용자 인증 토큰을 가져오도록 요청합니다.

<u>예상 결과</u>:

* 주문 및 협상 가능 견적은 의 사용자가 발주하지 않습니다. *차단됨* 회사.
* 의 사용자에 대한 인증 토큰을 가져올 수 없습니다. *거부됨* 회사.
* 에 대한 인증 토큰을 가져올 수 없습니다. *비활성* 고객.

<u>실제 결과</u>:

* 주문 및 협상 가능 견적은 의 사용자가 지정합니다. *차단됨* 회사.
* 인증 토큰은 의 사용자에 대해 획득됩니다. *거부됨* 회사.
* 다음에 대한 인증 토큰을 얻음: *비활성* 고객.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
