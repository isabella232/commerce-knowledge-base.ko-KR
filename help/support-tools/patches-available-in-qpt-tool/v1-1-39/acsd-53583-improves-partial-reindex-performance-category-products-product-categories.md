---
title: '''ACSD-53583: 의 부분 색인 재지정 성능 개선 [!UICONTROL Category Products] 및 [!UICONTROL Product Categories] 인덱서'
description: ACSD-53585 패치를 적용하여 범주 제품 및 제품 범주 인덱서에 대한 부분 색인 재지정 성능을 개선합니다.
feature: Products, Categories
role: Admin, Developer
exl-id: 1c8f7df3-379f-42d6-8b41-286d34f725d2
source-git-commit: 29c2918ccae6404f6ae87d360ac16b149de5dd0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53583: 카테고리 제품 및 제품 카테고리 인덱서에 대한 부분 색인 재지정 성능 개선

ACSD-53583 패치는 의 부분 색인 재지정 성능을 개선합니다. *범주 제품* 및 *제품 범주* 인덱서입니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.39가 설치되었습니다. 패치 ID는 ACSD-53583입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p3
* 과(와) 호환되지 않음 [!DNL Live Search] 모듈. 이 패치를 적용할 위치 [!DNL Live Search] 설치 시 추가 ACSD-55719 패치를 요청하십시오.

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

부분 색인 재지정은 전체 색인 재지정보다 시간이 더 걸립니다.

<u>재현 단계</u>:

1. 모든 인덱서를 다음으로 전환 *예약별 업데이트*.
1. 를 사용하여 데이터 생성 [!DNL Performance Toolkit] (중간 프로필).
1. 인덱스 백로그에 있고 모든 인덱스가 유휴 상태가 되도록 모든 제품 및 범주를 변경합니다.
1. 다음에 대한 부분 색인 재지정 수행 *범주 제품* 및 *제품 범주* 인덱서입니다.

<u>예상 결과</u>:

부분 리인덱스는 제품당 한 번 호출되며 모든 제품과 카테고리가 변경되었기 때문에 전체 리인덱스와 거의 동일한 시간이 소요된다.

<u>실제 결과</u>:

부분 리인덱스는 제품당 여러 번 호출되며 전체 리인덱싱보다 시간이 더 많이 소요된다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
