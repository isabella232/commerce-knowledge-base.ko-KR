---
title: 'ACSD-56741: 사용자 지정 MySQL 트리거로 데이터베이스 설정 오류 문제 해결'
description: ACSD-56741 패치를 적용하여 인덱싱과 관련이 없는 데이터베이스의 사용자 정의 MySQL 트리거로 인해 'setup:upgrade' 도중 null 유형의 값에 대한 배열 오프셋에 액세스하려고 함* 오류 메시지가 표시되는 Adobe Commerce 문제를 해결합니다. [!DNL MView].
feature: Install
role: Admin, Developer
source-git-commit: 216ce1035584e4c049029073ee0017d3616cdbd6
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56741: 사용자 지정 MySQL 트리거로 데이터베이스 설정 오류 문제 해결

ACSD-56741 패치는 오류 메시지가 표시되는 문제를 해결합니다 *null 유형의 값에 대한 배열 오프셋에 액세스하려고 합니다.* 다음 기간 동안 표시: `setup:upgrade` 인덱싱과 관련 없는 데이터베이스의 사용자 지정 MySQL 트리거로 인해 [!DNL MView]. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48이 설치되었습니다. 패치 ID는 ACSD-56741입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

오류 메시지 *null 유형의 값에 대한 배열 오프셋에 액세스하려고 합니다.* 다음 기간 동안 표시: `setup:upgrade` 인덱싱과 관련 없는 데이터베이스의 사용자 지정 MySQL 트리거로 인해 [!DNL MView].

<u>재현 단계</u>:

1. 실행 `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. 실행 `php bin/magento c:f`.
1. 실행 `php bin/magento setup:upgrade`.

<u>예상 결과</u>:

설치 업그레이드가 오류 없이 완료됩니다.

<u>실제 결과</u>:

설치 업그레이드가 종료되고 다음 오류 메시지가 표시됩니다.

*경고: null 유형의 값에 대한 배열 오프셋에 액세스하려고 합니다.*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
