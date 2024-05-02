---
title: "ACSD-51845: 비동기 벌크를 통해 계층 가격 및 다른 속성 세트로 후속 제품을 업데이트할 수 없음 [!DNL API]"
description: ACSD-51845 패치를 적용하여 계층 가격 및 다른 속성 세트를 통해 후속 제품을 업데이트할 수 없는 Adobe Commerce 문제를 해결합니다 [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845: 비동기화 벌크를 통해 계층 가격 및 다른 속성 세트로 후속 제품을 업데이트할 수 없음 [!DNL API]

ACSD-51845 패치는 비동기 벌크를 통해 계층 가격 및 다른 속성 세트로 후속 제품을 업데이트할 수 없는 문제를 해결합니다 [!DNL REST API]. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있습니다. 패치 ID는 ACSD-51845입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

비동기 벌크를 통해 계층 가격과 다른 속성 세트를 가진 후속 제품에 대한 업데이트가 실패합니다. [!DNL REST API].

<u>재현 단계</u>:

1. 구성 [!DNL RabbitMQ].
1. 두 개의 속성 세트를 만듭니다.
1. 2개 만들기 **단순 제품**, 각 제품을 다른 속성 세트에 할당합니다.
1. 추가 **고객 그룹 가격** 각 제품마다.
1. 두 제품을 동일한 벌크로 업데이트 [!DNL API] 업데이트.
1. 다음을 확인하십시오. `bin/magento queue:consumers:start async.operations.all` 명령이 실행 중입니다.
1. 벌크 확인 [!DNL API] 상태.

<u>예상 결과</u>:

서비스가 정상적으로 실행되었습니다.

<u>실제 결과</u>:

시스템이 다음 오류 메시지를 반환합니다. *제품을 저장할 수 없습니다. 다시 시도하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
