---
title: 설치 실패. install.log를 만들 수 없음
description: 이 문서에서는 설치 중에 설치 마법사가 'install.log'를 만들지 않아 실패한 설치에 대한 수정 사항을 제공합니다.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 설치 실패. install.log를 만들 수 없음

이 문서에서는 설치 마법사에서 다음을 만들지 않았기 때문에 실패한 설치에 대한 수정 사항을 제공합니다. `install.log` 설치하는 동안.

## 문제

Adobe Commerce 프로세스를 동시에 실행하면 설치 로그를 만드는 데 문제가 발생할 수 있습니다. (예: 별도의 탭 페이지에 두 개의 서로 다른 설치)

## 원인

Installation-fails-not-create-install.log 설치 `open_basedir` 위치: `php.ini`. 설치 마법사는 [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) 임시 디렉터리의 값을 가져오기 위한 PHP 호출입니다. If [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) 은(는) 이(가) 지정한 디렉터리에 대한 연결을 거부하도록 설정되었습니다. `sys_get_temp_dir`, 설치에 실패합니다.
다음에 대한 설정을 검토하십시오. `open_basedir` 위치: `php.ini`. 설치 마법사는 [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) 임시 디렉터리의 값을 가져오기 위한 PHP 호출입니다. If [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) 은(는) 이(가) 지정한 디렉터리에 대한 연결을 거부하도록 설정되었습니다. `sys_get_temp_dir`, 설치에 실패합니다.


## 솔루션

문제를 해결하려면 다음 값을 변경합니다. `open_basedir` 웹 서버를 다시 시작합니다.

이 값을 변경하는 방법을 잘 모를 경우 다음 단계를 사용하십시오.

1. 아직 만들지 않은 경우 [phpinfo.php](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo).
1. 브라우저의 주소 또는 위치 필드에 다음 URL을 입력합니다. `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. 의 위치를 찾습니다. `php.ini`.     `php.ini` 는 일반적으로 로 지정됩니다. **구성 파일을 로드했습니다.** 표시되는 결과에서
1. 루트 권한이 있는 사용자로 다음을 엽니다. `php.ini` 텍스트 편집기에서.
1. 다음 값 찾기 `open_basedir` 바꿔주세요.
1. 변경 내용 저장 `php.ini`.
1. 웹 서버를 다시 시작합니다.
