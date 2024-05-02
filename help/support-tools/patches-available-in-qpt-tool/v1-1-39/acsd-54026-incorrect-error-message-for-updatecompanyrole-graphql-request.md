---
title: 'ACSD-54026: updateCompanyRole GraphQL 요청에 대한 잘못된 오류 메시지'
description: ACSD-54026 패치를 적용하여 권한이 없는 사용자에 대한 updateCompanyRole GraphQL 요청에 대해 잘못된 오류 메시지가 있는 Adobe Commerce 문제를 수정합니다.
feature: Roles/Permissions
role: Admin, Developer
exl-id: c18a8815-975a-499d-a372-8635d89aa673
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-54026: 잘못된 오류 메시지 `updateCompanyRole` GraphQL 요청

ACSD-54026 패치는에 잘못된 오류 메시지가 있는 문제를 해결합니다. `updateCompanyRole` 권한이 없는 사용자에 대한 GraphQL 요청입니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.39가 설치되었습니다. 패치 ID는 ACSD-54026입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

에 대해 잘못된 오류 메시지를 가져오는 중 `updateCompanyRole` 권한이 없는 사용자에 대한 GraphQL 요청입니다.

<u>재현 단계</u>:

1. 구성에서 B2B 회사를 활성화합니다.
1. 회사를 만듭니다.
1. 보내기 `updateCompanyRole` 전달자 토큰을 전달하지 않거나 잘못된 전달자 토큰이 있는 GraphQL 요청.
1. GraphQL 응답에서 오류 메시지를 확인합니다.

<u>예상 결과</u>:

다음과 같은 오류 메시지가 표시됩니다. *현재 고객은 권한이 없습니다.*

<u>실제 결과</u>:

다음과 같은 오류 메시지가 표시됩니다. *고객이 회사 사용자가 아닙니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
