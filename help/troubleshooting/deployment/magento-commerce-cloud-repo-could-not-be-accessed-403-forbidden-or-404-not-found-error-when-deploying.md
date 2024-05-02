---
title: '클라우드 저장소의 Adobe Commerce에 액세스할 수 없음: 배포 시 403 금지됨 또는 404 찾을 수 없음 오류'
description: '이 문서에서는 다음과 유사한 클라우드 인프라의 Adobe Commerce 실패 배포 오류를 해결하는 방법에 대해 설명합니다.'
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# 클라우드 저장소의 Adobe Commerce에 액세스할 수 없습니다. 배포 시 403 금지됨 또는 404 찾을 수 없음 오류

이 문서에서는 다음과 유사한 클라우드 인프라의 Adobe Commerce 실패 배포 오류를 해결하는 방법에 대해 설명합니다.

&quot;*&#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL에 액세스할 수 없음: HTTP/1.1 403 금지됨* &quot;. 또는 &quot;*https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip&quot; 파일을 다운로드할 수 없음(HTTP/1.1 404 찾을 수 없음)*&quot;.

## 영향을 받는 제품 및 버전

* 클라우드 인프라 2.2.x, 2.3.x 및 2.4.x의 Adobe Commerce

## 문제

저장소 URL에 액세스할 수 없음을 나타내는 배포 시 오류 메시지가 표시됩니다.

<u>재현 단계</u>

수동으로 또는 환경의 병합, 푸시 또는 동기화를 수행하여 배포를 트리거합니다.

<u>실제 결과</u>

배포가 중단되었습니다. 프로젝트 UI의 배포 오류 로그에 다음과 유사한 오류 메시지가 표시됩니다.

*&quot;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL에 액세스할 수 없습니다. HTTP/1.1 \[403 금지됨 또는 404 찾을 수 없음\]&quot;*.

(로그를 보려면 프로젝트 UI에서 &quot;실패&quot; 아이콘을 클릭합니다.)

<u>예상 결과</u>

배포가 완료되었습니다.

## 원인

이 오류는 인증 키(액세스 키)가 잘못되었거나, 지정되지 않았거나, 올바르게 지정되지 않았기 때문에 발생합니다.

키가 유효하지 않은 이유 중 일부는 다음과 같습니다.

* 공유 계정을 사용하여 키를 생성했습니다.
* 귀하의 라이선스는 지불 문제로 인해 이전에 취소되었습니다.

>[!NOTE]
>
>송장 발행 또는 만료된 계약 문제로 인해 발생한 경우 Adobe 계정 팀에 문의하여 이를 해결하기 위한 지침을 확인하십시오. 라이센스가 다시 활성화되면 지원 및 배포 권한이 복원됩니다.

## 솔루션

다음 단계를 수행하여 인증 키 문제를 해결하십시오(각 단계에 대한 자세한 내용은 아래 섹션 참조).

1. 유효한 인증 키를 얻습니다(키가 유효하다고 확신하는 경우 건너뛰십시오).
1. 에 키 값 추가 `env:COMPOSER_AUTH` 변수(또는 올바른 값이 있는지 확인)를 시작하고 키가 변수에서 일관되게 지정되었는지 확인합니다. `auth.json` 프로젝트 루트에 있는 파일입니다.
1. 업데이트 또는 삭제 `auth.json`인증 키 값이 지정되지 않았거나 다른 값이 있는 경우 키가 구성되는 단일 위치를 갖도록.

### 1. 유효한 인증 키 얻기

공유 계정으로 만든 키를 사용하는 경우 액세스 권한을 제공하는 Adobe Commerce 라이선스 소유자에게 연락하여 키 생성을 요청해야 합니다.

결제 문제로 인해 이전에 라이선스가 취소된 후 해당 문제를 해결했으며 라이선스가 갱신되었다면 다음을 수행해야 합니다. [새 인증 키 생성](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html).

### 2. env:COMPOSER\_AUTH 변수에 키 값을 추가하고 auth.json에 동일한 키가 지정되어 있는지 확인합니다

의 지침 및 관련 정보를 참조하십시오. [기존 시스템 준비](https://devdocs.magento.com/cloud/setup/first-time-setup-import-prepare.html#auth-json) 및 [인증 키 추가](https://devdocs.magento.com/cloud/setup/first-time-setup-import-prepare.html#add-authentication-keys) 개발자 설명서에서 확인할 수 있습니다.

### 3. auth.json 업데이트 또는 삭제

다음은 인증 키를 업데이트하는 방법에 대한 단계별 설명입니다.

1. 클라우드 인프라의 Adobe Commerce SSH 키가 있는 컴퓨터에 로그인합니다.
1. 프로젝트에 로그인: `magento-cloud login`
1. 코드를 업데이트할 분기를 만듭니다(다음 예에서 분기 이름은 입니다). `auth` 기본 분기에서 만들어짐):     `magento-cloud environment:branch auth master`
1. 프로젝트 루트 디렉토리로 변경합니다.
1. 선택 사항: `auth.json` 원하는 경우 계속 [9단계](#step9).
1. 열기 `auth.json` 텍스트 편집기에서.

   ```json
              {
                "http-basic":  {
                    "repo.magento.com": {
                        "username": "<public_key>",
                        "password": "<private_key>"
                        }
                      }
                    }
   ```

1. 올바른 인증 키를 추가합니다.
1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 변경 내용 커밋 및 병합:

   `git add -A`

   `git commit -m "<message>"`

   `git push origin master`
1. 프로젝트가 배포될 때까지 기다립니다.
