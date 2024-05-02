---
title: '''ACSD-51739: ''CompanyTeam'' GraphQL 요청에서 ''structure_id'' 요청 오류'''
description: ACSD-51739 패치를 적용하여 'CompanyTeam' GraphQL 요청에서 'structure_id'가 요청되면 오류가 반환되는 Adobe Commerce 문제를 수정합니다.
exl-id: 31c085e0-c8be-4709-9620-80ff360dca9a
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739: 요청 시 오류 발생 `structure_id` 위치: `CompanyTeam` GraphQL 요청

ACSD-51739 패치는 다음과 같은 경우 오류가 반환되는 문제를 해결합니다. `structure_id` 다음 위치에 요청됨: `CompanyTeam` GraphQL 요청. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34가 설치되어 있습니다. 패치 ID는 ACSD-51739입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음 경우에 오류가 반환됩니다. `structure_id` 다음 위치에 요청됨: `CompanyTeam` GraphQL 요청.

<u>재현 단계</u>

1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**, 및 설정 *[!UICONTROL Enable Company]* 끝 *예*.
1. 회사 관리자 사용자와 함께 회사를 만듭니다.
1. 새 고객 만들기(*customer1*)를 만들고 (위에서 만든) 회사를 이 고객에게 할당합니다.
1. 프론트엔드에서 회사 관리자로 로그인합니다.
1. 회사 팀 만들기 및 할당 *customer1* 끌어다 놓기를 사용하여 팀에 연결할 수 있습니다.
1. 다음을 포함하는 다음 회사 GraphQl 쿼리를 실행합니다. `CompanyTeam` 포함 `structure_id`:

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. GraphQL 응답을 확인합니다.

<u>예상 결과</u>:

오류가 반환되지 않고 요청된 모든 데이터가 GraphQL 응답에 있습니다.

<u>실제 결과</u>:

* 응답에 다음 항목이 포함됨: *내부 서버 오류*.
* `var/log/exception.log` 포함:

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
