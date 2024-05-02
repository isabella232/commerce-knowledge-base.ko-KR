---
title: 성능 저하, 느리고 오래 실행되는 크론
description: 이 문서에서는 플랫 테이블 및 인덱서가 활성화되었기 때문에 사이트 성능 문제와 느린 실행 및 멈춤 크론을 해결하는 방법에 대해 설명합니다.
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 성능 저하, 느리고 오래 실행되는 크론

>[!WARNING]
>
>모든 Adobe Commerce 버전에서 일부 확장은 플랫 테이블에서만 작동하므로 플랫 테이블을 비활성화하면 위험이 있습니다. 플랫 카탈로그 인덱서를 사용하는 확장이 있는 경우 이러한 값을 &quot;로 설정할 때 이를 고려해야 할 수 있습니다. *아니요* &quot;.

이 문서에서는 사이트 성능 문제 및 로 인해 발생하는 느린 실행 및 중단 문제를 해결하는 방법에 대해 설명합니다. [플랫 테이블 및 인덱서](https://docs.magento.com/m2/ce/user_guide/catalog/catalog-flat.html) 활성화되었습니다.

영향을 받는 제품 및 버전

* cloud infrastructure 2.1.x 이상 버전의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.1.x 이상
* Magento Open Source 2.1.x 이상

## 문제

플랫 인덱서로 인해 다음이 발생할 수 있습니다.

* 많은 SQL 로드 및 사이트 성능 문제
* 오래 달리고 크론에 갇혀 있습니다.

## 원인

플랫 테이블 및 인덱서가 활성화되었습니다.

## 솔루션 {#solution}

Adobe Commerce 및 Magento Open Source 2.1.x 이상부터 플랫 카탈로그를 사용하는 것이 더 이상 모범 사례가 아니므로 권장되지 않습니다. 이 기능을 계속 사용하면 성능 저하 및 기타 인덱싱 문제가 발생하는 것으로 알려져 있습니다. 플랫 카탈로그를 비활성화하려면 다음을 수행합니다.

1. 관리자에서 다음 위치로 이동합니다. **스토어** > **설정** > **구성**.
1. 왼쪽 아래에 있는 패널에서 **카탈로그** , 선택 **카탈로그**.
1. 확장 **상점 첫 화면** 섹션을 참조하고 다음을 수행합니다.
   * 설정 **플랫 카탈로그 범주 사용** 끝 *아니요*.
   * 설정 **플랫 카탈로그 제품 사용** 끝 *아니요*.
1. 완료되면 다음을 클릭하십시오. **구성 저장**. 그런 다음 메시지가 표시되면 캐시를 새로 고칩니다.
1. 다음을 실행하여 캐시 초기화 `php bin/magento cache:flush`.

변경할 수 없는 경우 **플랫 카탈로그 범주 사용** 및 **플랫 카탈로그 제품 사용** 끝 *아니요* 옵션이 회색으로 표시되어 있으므로 의 플랫 인덱서를 비활성화하십시오. `app/etc/config.php`:

1. 이 명령을 실행하여 모든 인덱서가 예약에 의해 업데이트로 설정되었는지 확인합니다. `php bin/magento indexer:set-mode schedule`.
1. 편집 `app/etc/config.php` 다음 줄을 찾습니다. `flat_catalog_product` 및 `flat_catalog_category` - 비활성화하려면 1에서 0으로 변경합니다.
1. 명령 실행 `php bin/magento app:config:import`
1. 이 명령을 실행하여 플랫 인덱서가 비활성화되었는지 확인합니다. `php        bin/magento indexer:status`.
1. 다음을 실행하여 캐시 초기화 `php bin/magento cache:flush`.

## 관련 정보

[클라우드에서 수동으로 중단된 Adobe Commerce cron 작업 재설정](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md) 을 참조하십시오.
