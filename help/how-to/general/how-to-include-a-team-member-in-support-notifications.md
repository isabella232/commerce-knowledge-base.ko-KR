---
title: 지원 알림에 팀원을 포함하는 방법
description: 이 문서에서는 지원 알림에 팀원을 포함하는 방법에 대한 설명을 제공합니다.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 1c568d75534bbfe322d9f980b40c5dd64fc5b7a2
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 지원 알림에 팀원을 포함하는 방법

이 문서에서는 팀 구성원이 이메일 알림을 통해 지원 업데이트를 자동으로 받도록 하는 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모두 [지원되는 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## 원인

* 팀원이 다음에 추가되지 않았습니다. [!DNL cloud project] 필요한 권한과 함께.
* 팀원에게 지원 계정이 없습니다.

## 솔루션

1. 로 이동 **[!DNL Cloud Project URL]** (예: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. 팀원이 프로젝트에 추가되었고 이(가) [!DNL Super User].

필요하지 않은 경우 [!DNL cloud project] 액세스, 제출 [Adobe Commerce 지원 센터의 지원 요청](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 자동으로 참조: 모든 티켓에서 참조하며 **[!DNL MAGE ID]** (가능한 경우).

프로젝트에 추가되지 않은 경우 (으)로 추가해야 합니다. [!DNL Super User] 및 부여 [!DNL Shared Access]:

* [사용자 액세스 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) 사용 안내서에서 참조하십시오.
* [Adobe Commerce 클라우드 프로젝트에 사용자를 추가할 수 없음](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) Commerce 기술 자료.
* [Adobe Commerce 도움말 센터 사용 안내서: 공유 액세스](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) Commerce 기술 자료.

항목이 다음에 추가된 경우 [!DNL cloud project], 하지만 은(는) [!DNL Super User role], 업데이트 [!DNL role] 이에 따라 [사용자 액세스 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## 관련 읽기

[이전 팀원이 Adobe Commerce 클라우드 알림 이메일을 받습니다.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
