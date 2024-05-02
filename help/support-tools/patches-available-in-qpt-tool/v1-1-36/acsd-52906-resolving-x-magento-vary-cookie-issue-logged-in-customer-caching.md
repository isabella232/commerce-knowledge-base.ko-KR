---
title: 'ACSD-52906: 로그인한 고객 캐싱에 대한 X-Magento-Vary 쿠키 문제 해결'
description: ACSD-52906 패치를 적용하여 로그인한 고객에 대해 X-Magento-Vary 쿠키가 잘못 설정된 Adobe Commerce 문제를 수정합니다.
feature: Cache
role: Admin, Developer
exl-id: 863e0808-9208-467d-8d56-9dd7a7f4354d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-52906: 로그인한 고객의 X-Magento-Vary 쿠키 문제 해결

ACSD-52906 패치는 로그인한 고객에 대해 X-Magento-Vary 쿠키가 잘못 설정되는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.36이 설치되었습니다. 패치 ID는 ACSD-52906입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

동일한 고객 Magento에 속하는 로그인한 고객에 대해 X-Segment-Vary 쿠키가 잘못 설정되어 일부 페이지에 부적절한 캐싱이 발생합니다.

<u>전제 조건</u>:

Adobe Commerce Inventory management(MSI) 모듈이 설치되고 활성화됩니다.

<u>재현 단계</u>:

1. 구성 [!DNL Varnish] 또는 [!DNL Fastly] 캐시입니다.
1. 새 고객 세그먼트를 만들고 *등록됨* 고객.
1. 두 개의 고객 (예: customer1 및 customer2)을 만듭니다.
1. 캐시를 지웁니다.
1. customer1로 로그인하고 홈 페이지로 이동합니다.
1. 브라우저에서 시크릿 페이지를 엽니다.
1. 홈 페이지 이외의 다른 페이지로 이동합니다.
1. customer2로 로그인
1. 홈 페이지로 이동합니다.
1. 페이지가 브라우저 개발 콘솔에서 캐시되는지 확인합니다.

<u>예상 결과</u>:

페이지가 캐시에서 검색됩니다.

<u>실제 결과</u>:

페이지가 캐시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
