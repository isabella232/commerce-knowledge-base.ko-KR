---
title: 클라우드 인프라에서 Adobe Commerce의 환경 재설정
description: 이 문서에서는 클라우드 인프라에서 Adobe Commerce의 환경을 롤백하는 다양한 시나리오를 보여 줍니다.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: ddde2385f1d94194b34e9ed51f6cbda55c916d90
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# 클라우드 인프라에서 Adobe Commerce의 환경 재설정

이 문서에서는 클라우드 인프라에서 Adobe Commerce의 환경을 롤백하는 다양한 시나리오를 보여 줍니다.

사용 사례에 가장 적합한 항목 선택:

* 활동을 계획한 경우(계획된 배포 또는 업그레이드) - [시나리오 1: 계획된 활동)](#scen1).
* 유효한 스냅샷이 있는 경우 - [시나리오 2: 스냅샷 복원](#scen2).
* 안정적인 빌드가 있지만 유효한 스냅샷이 없는 경우 - [시나리오 3: 스냅샷 없음, 안정적인 빌드(SSH 연결 사용 가능)](#scen3).
* 빌드가 손상되고 유효한 스냅숏이 없는 경우 - [시나리오 4: 스냅숏 없음, 빌드가 끊김(SSH 연결 없음)](#scen4).

## 시나리오 1: 계획된 활동

계획된 배포 또는 업그레이드를 통해 가장 쉽고 권장되는 작업 [!UICONTROL Rollback] 상인이 준비의 일환으로 다음과 같이 할 것입니다.

>[!NOTE]
>
>에서 이러한 단계를 항상 테스트하십시오. **[!UICONTROL Staging Environment]** 먼저!

<u>업그레이드/배포 활동 5일 전</u>:

1. 현재 데이터베이스의 크기를 확인합니다.
1. 에 디스크 공간이 충분한지 확인 `/data/exports` 을(를) 유지하려면 [!UICONTROL Database Dump]. 디스크 공간이 부족한 경우 원하지 않는 데이터를 제거하거나 지원 사례를 만들고 디스크를 확장하도록 요청합니다.

<u>변경 당일</u>:

1. 웹 사이트를 로 배치 [!UICONTROL Maintenance Mode].<br>
자세한 내용 [활성화 또는 비활성화 [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html) 사용 안내서에서 [[!UICONTROL Maintenance Mode] 업그레이드 옵션](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html) 업그레이드 안내서에서 확인할 수 있습니다.
1. 로컬 항목 사용 [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html).

<u>다음과 같은 경우 [!UICONTROL Rollback] 필수</u>:

1. 다음과 같은 응용 프로그램 [!DNL MariaDB] 이(가) 이 계획된 활동의 일부로 업그레이드되었습니다. 먼저 해당 애플리케이션을 이전 버전으로 다시 설치하십시오.
1. [!UICONTROL Rollback] 로컬을 사용하는 데이터베이스 [!UICONTROL Database Dump]및 로 다시 가져오기 [!DNL MariaDB].
1. [!UICONTROL Rollback] 를 통한 코드 [!DNL Git] 이전 작업 버전으로 마이그레이션 하는 것이 좋습니다.

사용 [!UICONTROL Snapshots] 은(는) 업그레이드/계획된 활동에 권장되는 방법이 아닙니다. [!UICONTROL rollbacks/restores]: 로컬에 비해 데이터를 검색하는 데 훨씬 오래 걸리기 때문입니다 [!UICONTROL Database Dump]의 2단계에서 위에서 설명한 대로 **다음과 같은 경우 [!UICONTROL Rollback] 필수** 섹션.

[!UICONTROL Snapshots] 노드/서버에 보관되지 않고 별도의 스토리지 블록에 보관되며, 이 데이터는 네트워크를 통해 블록 스토리지에서 새 디스크로 전송되어야 하므로 프로세스에 시간이 소요됩니다. 그런 다음 새 디스크가 노드/서버에 연결된 원본 디스크로 검색/가져올 준비가 된 노드에 마운트됩니다.

이것을 로컬 가져오기와 비교할 때 [!UICONTROL Database Dump]은 이미 노드/서버에서 데이터를 검색할 수 있으므로 많은 시간이 의 [!UICONTROL Database Import] 필수 항목입니다.

## 시나리오 2: 스냅샷 복원

읽기: [클라우드 인프라의 Adobe Commerce에서 스냅샷 복원](https://devdocs.magento.com/cloud/project/project-webint-snap.html#restore-snapshot) 개발자 설명서에서 확인할 수 있습니다.

>[!NOTE]
>
>클라우드 인프라 계정에서 Adobe Commerce에 액세스한 후 주요 변경 사항을 적용하기 전에 스냅샷을 만드는 것이 첫 번째 단계여야 합니다. 모범 사례이며 적극 권장합니다.

읽기: [스냅샷 만들기](https://devdocs.magento.com/cloud/project/project-webint-snap.html#create-snapshot) 개발자 설명서에서 확인할 수 있습니다.

## 시나리오 3: 스냅샷 없음, 안정적인 빌드(SSH 연결 사용 가능)

이 섹션에서는 스냅샷을 만들지 않았지만 SSH를 통해 환경에 액세스할 수 있는 경우 환경을 재설정하는 방법을 보여줍니다.

단계는 다음과 같습니다.

1. 구성 관리를 비활성화합니다.
1. Adobe Commerce 소프트웨어를 제거합니다.
1. 재설정 [!DNL git] 분기입니다.

다음 단계를 수행한 후:

* Adobe Commerce 설치가 바닐라 상태로 돌아갑니다(데이터베이스 복원됨, 배포 구성이 제거됨, 디렉터리 `var` 삭제).
* 사용자 [!DNL git] 분기는 과거의 원하는 상태로 재설정됩니다.

아래의 자세한 단계를 읽어 보십시오.

### 0단계 (전제 조건): 구성 관리를 비활성화하려면 config.php를 제거

배포 중에 이전 구성 설정을 자동으로 적용하지 않도록 구성 관리를 비활성화해야 합니다.

구성 관리를 비활성화하려면 `/app/etc/` 디렉터리에 다음 항목이 없습니다. `config.php` 파일.

구성 파일을 제거하려면 다음 단계를 수행하십시오.

1. [환경에 SSH 추가](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. 구성 파일을 제거합니다. `rm app/etc/config.php`

구성 관리에 대해 자세히 알아보십시오.

* [클라우드 인프라에서 Adobe Commerce의 배포 중단 시간 감소](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) 을 참조하십시오.
* [저장소 설정에 대한 구성 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) 개발자 설명서에서 확인할 수 있습니다.

### 1단계: setup:uninstall 명령을 사용하여 Adobe Commerce 소프트웨어 제거


Adobe Commerce 소프트웨어를 제거하면 데이터베이스가 삭제 및 복원되고, 배포 구성이 제거되며, 아래의 디렉토리가 지워집니다. `var`.

읽기: [Adobe Commerce 소프트웨어 제거](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) 개발자 설명서에서 확인할 수 있습니다.

Adobe Commerce 소프트웨어를 제거하려면 다음 단계를 따르십시오.

1. [환경에 SSH 추가](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. 실행 `setup:uninstall` : `bin/magento setup:uninstall`
1. 제거를 확인합니다.

성공적으로 제거되었음을 확인하는 메시지가 표시됩니다.

```php
[SUCCESS]: Magento uninstallation complete.
```

즉, Adobe Commerce 설치(DB 포함)를 실제(바닐라) 상태로 되돌렸습니다.

### 2단계: 재설정 [!DNL git] 분기

포함 [!DNL git] 재설정하면 코드를 이전의 원하는 상태로 되돌립니다.

1. 환경을 로컬 개발 환경에 복제합니다. 클라우드 콘솔에서 명령을 복사할 수 있습니다.    ![copy_git_clone.png](assets/copy_git_clone.png)
1. 커밋 내역에 액세스합니다. 사용 `--reverse` 더 많은 편의를 위해 내역을 역순으로 표시하려면 `git log --reverse`
1. 정상적으로 작업한 커밋 해시를 선택합니다. 코드를 실제 상태(바닐라)로 재설정하려면 분기(환경)를 만든 첫 번째 커밋을 찾습니다.
   ![Git 콘솔에서 커밋 해시 선택](assets/select_commit_hash.png)
1. 하드 적용 [!DNL git] 재설정: `git reset --h <commit_hash>`
1. 변경 사항을 서버에 푸시: `git push --force <origin> <branch>`

다음 단계를 수행한 후 [!DNL git] 분기가 재설정되고 전체 [!DNL git] 변경 로그가 명확합니다. 마지막 [!DNL git] 푸시 트리거는 재배포를 트리거하여 모든 변경 사항을 적용하고 Adobe Commerce을 다시 설치합니다.

## 시나리오 4: 스냅숏 없음, 빌드가 중단됨(없음) [!DNL SSH] connection)

이 섹션에서는 위험 상태일 때 환경을 재설정하는 방법을 보여줍니다. 배포 프로시저가 작업 응용 프로그램을 빌드할 수 없으므로 [!DNL SSH] 연결을 사용할 수 없습니다.

이 시나리오에서는 먼저 다음을 사용하여 Adobe Commerce 애플리케이션의 작업 상태를 복원해야 합니다. [!DNL git] 재설정한 다음 Adobe Commerce 소프트웨어를 제거합니다. 데이터베이스를 삭제하고 복원하려면 배포 구성을 제거하는 등 시나리오에는 시나리오 3과 동일한 단계가 포함되지만 단계 순서가 다르고 추가 단계인 강제 재배포가 있습니다. 단계는 다음과 같습니다.

1. [재설정 [!DNL git] 분기입니다.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [구성 관리를 비활성화합니다.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [Adobe Commerce 소프트웨어를 제거합니다.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. 강제 재배포.

이 단계를 수행하면 시나리오 3과 동일한 결과가 나옵니다.

### 4단계: 강제 재배포

커밋을 만들고(권장하지는 않지만 빈 커밋일 수 있음) 서버에 푸시하여 재배포를 트리거합니다.

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## 설치:제거가 실패하면 데이터베이스를 수동으로 재설정하십시오.

를 실행하는 경우 `setup:uninstall` 명령이 오류와 함께 실패하고 완료할 수 없습니다. 다음 단계를 수행하여 수동으로 DB를 지울 수 있습니다.

1. [환경에 SSH 추가](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. MySQL DB에 연결: `mysql -h database.internal` Pro 환경의 경우 다음을 참조하십시오. [MySQL 서비스 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)).
1. \&#39;main\` DB 를 삭제합니다. `drop database main;`
1. 빈 \`main\` DB 만들기: `create database main;`
1. 다음 구성 파일을 삭제합니다. `config.php` , `config.php` , `.bak,` , `env.php`, `env.php.bak`

DB를 재설정한 후 [만들기 [!DNL git] 환경에 푸시하여 재배포 트리거](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html) 새로 만든 DB에 Adobe Commerce을 설치합니다. 또는 [redeploy 명령 실행](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).
