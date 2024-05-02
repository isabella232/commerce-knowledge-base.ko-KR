---
title: 'MDVA-19640: 고급 보고에 데이터가 표시되지 않음'
description: MDVA-19640 패치는 고급 보고에 데이터가 표시되지 않을 때 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-19640입니다. 향후 버전에서는 이 문제를 해결할 계획이 없습니다.
exl-id: 6df70f10-5d34-4540-b2ae-3a0be32f2bfd
feature: Commerce Intelligence
role: Admin
source-git-commit: 2914a110444898f78d2ed43ea96a9c5f6e70229f
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# MDVA-19640: 고급 보고에 데이터가 표시되지 않음

MDVA-19640 패치는 고급 보고에 데이터가 표시되지 않을 때 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치되어 있습니다. 패치 ID는 MDVA-19640입니다. 향후 버전에서는 이 문제를 해결할 계획이 없습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.3.0

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.1 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 관리에서 **보고서** > **Business Intelligence** 및 선택 **고급 보고**.
1. 보기 **고급 보고** 페이지를 가리키도록 업데이트하는 중입니다.

<u>예상 결과</u>:

고급 보고 보고서에는 예상대로 정보가 포함되어 있습니다.

<u>실제 결과</u>:

고급 보고 보고서에 데이터가 표시되지 않습니다.

<u>패치 설치 후 추가 단계 필요</u>:

cron_schedule 테이블의 레코드를 업데이트하려면 다음 SQL 쿼리를 적용해야 합니다.
`UPDATE core_config_data SET path = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics") WHERE path LIKE "crontab/default/jobs/analytics%";`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
