---
title: 'ACSD-51892: 구성 파일이 여러 번 로드되는 성능 문제'
description: ACSD-51892 패치를 적용하여 배포 중에 구성 파일이 여러 번 로드되는 Adobe Commerce 성능 문제를 해결합니다.
feature: Observability
role: Admin
exl-id: 397343df-360f-43c4-bcef-be5f0da5aeef
source-git-commit: 97734799a39f41d0d6441379e21608fa5fcd1d4c
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-51892: 구성 파일이 여러 번 로드되는 성능 문제

ACSD-51892 패치는 를 로드할 때 발생하는 성능 문제를 해결합니다. `app/etc/env.php` 및 `app/etc/config.php` 배포 구성 값이 단일 요청 내에서 액세스될 때마다 파일에 액세스할 수 있습니다. 과도한 파일 읽기는 시스템에 부담을 주어 전반적인 성능이 저하됩니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.33이 설치되었습니다. 패치 ID는 ACSD-51892입니다. Adobe Commerce 2.4.6-p2에서 문제가 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 파일이 여러 번 로드되는 성능 문제가 있습니다.

<u>재현 단계</u>:

1. Adobe Commerce 2.4.6 이상으로 배포 또는 업그레이드합니다.
1. 파일 시스템 로그에서 액세스 확인 `app/etc/env.php` 및 `app/etc/config.php` 배포가 실행 중인 파일입니다.

<u>예상 결과</u>:

일반 일정 내에 배포가 성공했습니다.

<u>실제 결과</u>:

* 서버는 사용자가 입력하는 모든 명령에 응답하기 위해 어려움을 겪고 있습니다. 그 결과 다음이 발생합니다. *오류 503 첫 번째 바이트 시간 초과* 웹 사이트에 액세스할 때.
* 로그 파일에 액세스 권한이 있는 여러 항목이 있습니다. `app/etc/env.php` 및 `app/etc/config.php` 파일.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
