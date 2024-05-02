---
title: 클라우드의 Adobe Commerce에서 MySQL에 더 많은 공간 할당
description: 이 문서에서는 클라우드 인프라의 Adode Commerce에서 MySQL에 더 많은 공간을 할당하는 방법에 대한 지침을 제공합니다.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 클라우드의 Adobe Commerce에서 MySQL에 더 많은 공간 할당


## 스타터 플랜 및 Pro 플랜 통합에 공간 할당

모든 Starter 계획 환경 및 Pro 계획 [통합 환경](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)에서 MySQL에 더 많은 공간을 할당할 수 있습니다 `.magento/services.yaml` 파일, 를 늘려 `mysql: disk:` 매개 변수. For example:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

다음을 참조하십시오. [MySQL 서비스 설정](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-mysql.html) 참조 문서.

을(를) 변경하면 `.magento/services.yaml` 변경 사항을 적용하려면 변경 사항을 커밋하고 푸시해야 합니다. 푸시가 배포 프로세스를 트리거합니다.

>[!WARNING]
>
>스타터 플랜 파티션은 더 작게(예: 30GB에서 20GB로) 만들면 치명적인 데이터 손상이 발생할 수 있으므로 더 작게 만들면 안 됩니다.

## Pro 계획 스테이징 또는 프로덕션에 공간 할당

Pro 플랜의 스테이징 또는 프로덕션 환경에 대해 이러한 변경 작업을 수행하려면 다음을 만들어야 합니다. [지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). 스토리지 증가를 위해 지원 티켓을 제출할 때는 스토리지 적용 대상 파티션 (`/mysql` 또는 `/exports`). 스토리지 증가 요청을 수행하려면 Adobe 계정 팀의 승인이 필요하며, 계정 팀은 승인 전에 주문 양식에 따라 권한이 부여된 스토리지 양을 검토하게 됩니다.

## 할당된 공간 축소를 사용할 수 없음(Pro 및 Starter 계획)

Adobe Commerce 지원에서 파티션을 늘릴 수 있음(`/mysql` 또는 `/exports`). 그러나 파티션을 축소할 수는 없습니다. 이렇게 하면 데이터가 손상될 위험이 있으므로 파티션에 대한 저장 공간 축소를 사용할 수 없습니다.
또한 할당된 공간을 직접 늘릴 수 있는 스타터 플랜에도 적용됩니다. 줄이는 것은 권장되지 않으며 치명적인 데이터 손상을 초래할 수 있습니다.
