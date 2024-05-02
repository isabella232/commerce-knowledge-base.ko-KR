---
title: 클라우드 인프라에서 Adobe Commerce의 관리 URL 변경
description: 기본적으로 [Commerce Admin](https://docs.magento.com/m2/ee/user_guide/stores/admin.html) URL은 *&lt;domain\_name&gt;/admin*으로 설정됩니다. 이 문서에서는 URL을 변경하는 방법을 보여 줍니다.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 04dba4e2adeaaa7649b817444024bf96e7830ad3
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# 클라우드 인프라에서 Adobe Commerce의 관리 URL 변경

기본적으로 [Commerce 관리자](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) URL이 다음으로 설정됨 *&lt;domain _name=&quot;&quot;>/admin*. 이 문서에서는 URL을 변경하는 방법을 보여 줍니다.

## 방법 1: 관리자를 사용하여 변경

다음 단계를 읽어 보십시오. [사용자 지정 관리자 URL > 관리자의 변경 사용](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) 사용 안내서에서 참조하십시오.

## 방법 2: ADMIN\_URL 환경 변수 추가

### 통합 환경

다음에서 [클라우드 콘솔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html)를 클릭하고 새 변수를 추가합니다.

**이름:** ADMIN\_URL **값:** 새 관리자 URL

* 자세한 단계는 를 참조하십시오. [환경 변수 추가](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) 개발자 설명서에서 확인할 수 있습니다.
* 도 참조하십시오. [환경 변수](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) 개발자 설명서에서 확인할 수 있습니다.

### 클라우드 콘솔에서 스테이징 및 프로덕션을 사용할 수 없는 경우

[지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 스테이징 또는 프로덕션 환경에 대한 ADMIN\_URL 변수 추가 요청.

클라우드 콘솔에서 스테이징 및 프로덕션에 액세스할 수 있는 경우 *통합 환경* 위의 섹션.

### Cloud CLI를 사용하여 변수 추가

다음 Cloud CLI 명령(기본)을 사용하여 ADMIN\_URL 변수를 추가할 수 있습니다.

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

자세한 지침은 다음을 참조하십시오. [관리자 URL 변경](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) : Commerce on Cloud Infrastructure 안내서의 관리자 변수 항목.

Cloud CLI를 사용하여 ADMIN\_URL 변수를 변경하면 환경의 재배포가 트리거됩니다. 변수는 기본적으로 상속할 수 있습니다. 상속을 방지하려면 Cloud CLI 명령 옵션을 사용하여 변수 값을 하위 환경에서 상속하지 않도록 하십시오. 다음을 참조하십시오. [가시성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) Commerce on Cloud Infrastructure 안내서의 변수 수준 항목.
