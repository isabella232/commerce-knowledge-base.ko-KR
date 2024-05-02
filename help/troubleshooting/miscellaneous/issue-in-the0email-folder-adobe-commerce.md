---
title: 클라우드에서 변수/내보내기 폴더 권한 문제 Adobe Commerce
description: 이 문서에서는 'var/export/email' 폴더의 서버에 대한 파일 권한 문제로 인해 제품 데이터를 내보낼 수 없는 문제에 대한 해결 방법을 제공합니다. 증상에는 사용자 인터페이스에서 사용할 수 없는 제품 및 카탈로그 내보내기가 포함되지만 SSH를 사용할 때에는 표시됩니다.
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 클라우드에서 변수/내보내기 폴더 권한 문제 Adobe Commerce

이 문서에서는 의 서버에 대한 파일 권한 문제로 인해 제품 데이터를 내보낼 수 없는 문제에 대한 해결 방법을 제공합니다 `var/export/email` 폴더를 삭제합니다. 증상에는 사용자 인터페이스에서 사용할 수 없는 제품 및 카탈로그 내보내기가 포함되지만 SSH를 사용할 때에는 표시됩니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## 문제

에서 파일을 내보낼 수 없습니다. `var/export/email` 또는 `var/export/archive` 폴더를 삭제합니다.
다음에 대한 권한으로 인해 배포가 실패했습니다. `var/export/email` 또는 `var/export/email/archive` 해당 아카이브 폴더는 이메일에 작성되며 내보내기/이메일만 수행하는 경우 하위 폴더 계정에 항목을 추가하는 것 이외의 문제가 있을 수 있습니다 `var/export/email/archive`.

<u>재현 단계</u>:

관리에서 **시스템** > *데이터 전송* > **내보내기**.
에 저장할 CSV 파일 선택 `var/export/` 폴더를 삭제합니다.

<u>예상 결과</u>:

CSV 파일이 표시되며 내보낼 수 있습니다.

<u>실제 결과</u>:

CSV 파일이 표시되지 않습니다. 또한 권한 거부 메시지가 표시됩니다. *RecursiveDirectoryIterator::__construct(/app/project id>/var/export/email): 디렉토리를 열지 못했습니다. 권한이 거부되었습니다.*

모든 내보내기 유형(Advanced Pricing, 고객 재무, 고객 기본 파일 및 고객 주소)에 대해 동일한 메시지를 받게 됩니다.

## 원인

이 문제는 내부에 생성된 폴더로 인해 발생합니다 `/var` 권한이 불완전한 경우: `d-wxrwsr-T`. T 고정 비트는 사용자가 소유한 파일만 삭제할 수 있음을 의미하지만, 실행 파일이 없으면 디렉터리에 파일을 만들 수 없음을 의미합니다.

이 문제는 시스템에서 이라는 폴더를 만들 때 자주 표시됩니다. `export`: 라는 폴더가 있는 경우 `email`: 라는 폴더가 있는 경우 `archive`.

디렉토리에 이러한 잘못 구성된 권한이 있는지 확인하려면 CLI/Terminal에서 다음 명령을 실행합니다.

`ls -ld var/export/`

권한이 잘못 구성된 경우 출력은 다음과 같습니다.

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## 솔루션

이 문제를 해결하려면 다음 명령을 실행하여 폴더의 권한을 777로 업데이트한 다음 모든 파일을 재귀적으로 업데이트합니다.

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## 관련 읽기

* [내보내기](https://docs.magento.com/user-guide/system/data-export.html) 사용 안내서에서 참조하십시오.
