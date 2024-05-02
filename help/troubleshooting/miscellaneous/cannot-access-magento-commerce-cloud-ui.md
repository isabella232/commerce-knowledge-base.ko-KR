---
title: 클라우드 인프라 UI에서 Adobe Commerce에 액세스할 수 없음
description: 이 문서에서는 클라우드 인프라 UI에서 Adobe Commerce에 로그인하지 못하고 "403 오류"가 발생하는 문제에 대한 해결 방법을 제공합니다.
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: 3d3d2da45d164efbbbaf8c878967caf83f845a59
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 클라우드 인프라 UI에서 Adobe Commerce에 액세스할 수 없음

이 문서에서는 클라우드 인프라 UI에서 Adobe Commerce에 로그인하고 를 가져올 수 없는 문제에 대한 해결 방법을 제공합니다. *403 오류*.

## 문제

클라우드 인프라 UI에서 Adobe Commerce에 처음 로그인하면 *403: 환경 액세스 거부됨* 오류. 이 오류는 클라우드 URL로 처음 이동하면 마스터 분기가 로드되기 때문에 발생할 수 있으며, 해당 분기에 대한 액세스 권한이 없을 수 있습니다.

## 솔루션

URL에 처음 액세스할 때 403 오류가 발생하는 경우 마스터 분기에 역할이 있는지 확인하십시오.

1. 프로젝트с의 라이선스 소유자 또는 슈퍼 사용자에게 연락하여 (으)로 귀하에게 액세스 권한을 제공했는지 확인하십시오. **환경 수준 사용자**,에 설명됨 [클라우드 프로젝트 > Cloud Console에서 사용자 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-cloud-console) 개발자 설명서에서 확인할 수 있습니다.

   특정 분기에 적용 가능한 역할만 있는 경우 해당 분기의 URL로 이동해야 합니다. 예:
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   다음에 기본 URL에 액세스할 때 이 URL은 기본적으로 마지막으로 방문한 환경으로 설정됩니다.

1. 여전히 로그인할 수 없는 경우 프로젝트с의 라이선스 소유자 또는 슈퍼 사용자에게 연락하여 (으)로 액세스 권한을 제공했는지 확인하십시오. **프로젝트 수준 사용자**&#x200B;에 설명된 대로 [클라우드 프로젝트 > 프로젝트에 사용자 추가](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-a-user-to-the-project) 개발자 설명서에서 확인할 수 있습니다.
1. 오류가 지속되면 [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
