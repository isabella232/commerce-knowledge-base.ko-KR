---
title: 최신 Beta 버전에 액세스할 수 없음
description: 이 문서에서는 Adobe Commerce용 코드의 최신 Beta 버전을 활용하려고 할 때 발생하는 문제에 대한 솔루션을 제공합니다. 베타 코드는 [Adobe Commerce 베타 프로그램](https://github.com/magento/magento2/wiki/Magento-Beta-Program)에 설명된 프로세스를 수행한 공식 Adobe 파트너에 대해서만 사용할 수 있습니다.
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# 최신 Beta 버전에 액세스할 수 없음

이 문서에서는 Adobe Commerce용 코드의 최신 Beta 버전을 활용하려고 할 때 발생하는 문제에 대한 솔루션을 제공합니다. 베타 코드는에 설명된 프로세스를 수행한 공식 Adobe 파트너에 대해서만 사용할 수 있습니다. [Adobe Commerce 베타 프로그램](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## 문제

이 문서에서는 조기 액세스 코드 액세스와 관련된 다음 문제를 다룹니다.

* Adobe Commerce 베타 버전은 다음에서 다운로드할 수 없습니다. **내 계정** > **다운로드** 날짜 [magento.com](https://account.magento.com/customer/account/login).
* 에서 조기 액세스 Adobe Commerce 버전을 다운로드하지 못했습니다. [magento.com](https://account.magento.com/customer/account/login) 작성기를 사용합니다.

## 원인

다음은 문제의 가장 일반적인 원인입니다.

* 잘못된 위치에서 조기 액세스 코드를 찾고 있습니다.
* 잘못된 MageID를 사용하고 있습니다.
* 개발자는 올바른 MageID의 액세스 키가 필요합니다.
* 계정이 Beta 프로그램의 일부가 아닙니다.

## 솔루션

### 조기 액세스 코드 위치

Beta 액세스 기간 동안에는 의 Composer를 통해서만 릴리스 패키지를 사용할 수 있습니다. [repo.magento.com](https://repo.magento.com/). 이 기간 동안 GitHub 및 Adobe Commerce 포털에서 릴리스 패키지를 사용할 수 없으며 GA 날짜에 이러한 위치에 게시합니다. Composer 사용 방법에 대한 자세한 내용은 [여기](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html).

### 사용해야 하는 MageID

파트너 계정과 연결된 기본 MageID를 사용해야 합니다. Beta 프로그램이 공유 액세스 권한이 있는 연락처와 연결되어 있지 않습니다. 조기 액세스는 작성기 또는 [repo.magento.com](https://repo.magento.com/) 파트너 라이선스와 연결된 MageID별.

#### 내 MageID가 기본 ID인지 어떻게 알 수 있습니까?

MageID가 기본 인지 확인하려면 다음을 시도해 보십시오.

1. 에 로그인 [magento.com](https://account.magento.com/customer/account/login) 로 이동 **내 제품 및 서비스** 탭. Partners 하위 섹션에서 활성 Partner 라이센스 정보가 표시되는지 확인합니다.
   * 활성 파트너 라이센스 정보가 표시되면 MageID는 기본 입니다. END DATE 값이 미래의 날짜인 경우 Partner 라이센스가 활성화됩니다.
   * 활성 파트너 라이선스 정보가 표시되지 않으면 MageID에는 공유 액세스만 있습니다. 기본 ID 보유자를 확인하려면 **나와 공유됨** SHARENAME이 지정된 것을 확인합니다. 클릭 **계정 전환** SHARENAME에서 지정한 값을 선택합니다. 시작 페이지에 기본 ID 소유자의 이메일이 표시됩니다.
1. 어떤 이유로든 다음 정보를 찾을 수 없습니다. [magento.com](https://account.magento.com/customer/account/login), 파트너 관리자에게 문의하십시오.
1. 위의 방법 중 어느 것도 효과가 없으면 [지원 문의](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### 개발자가 키에 올바르게 액세스할 수 없음

기본 MageID 소유자이고 팀의 개발자에게 액세스 권한을 부여해야 하는 경우 아래 단계를 따르십시오.

1. 기본 MageID 소유자가에 로그인하도록 합니다. [account.magento.com](https://account.magento.com/customer/account/login).
1. 다음 항목 선택 **마켓플레이스** tab을 누른 다음 **액세스 키**.
1. 선택 **새 액세스 키 만들기** 이름을 지정합니다.
1. 개발자에게 키를 보냅니다.

### 조기 액세스 프로그램의 일부가 아님

Beta 액세스 프로그램은 솔루션 및 기술 파트너만 사용할 수 있으므로 사전 프로덕션 코드를 평가할 수 있습니다. Beta Access 프로그램에 포함되려면 귀사는 현재 상태가 양호하고 베타 NDA에 서명한 활성 Adobe 파트너 계정이 있어야 합니다 [여기](https://github.com/magento/magento2/wiki/Magento-Beta-Program). 이러한 기준을 충족한다고 판단되어 베타 코드에 액세스할 수 없는 경우 다음 주소로 문의하십시오. [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
