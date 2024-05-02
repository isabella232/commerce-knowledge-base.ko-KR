---
title: '클라우드의 Adobe Commerce: 인증 키 변경 및 재배포'
description: 이 문서에서는 다양한 인증 키를 사용하여 클라우드 인프라에 Adobe Commerce을 다시 배포하는 방법에 대한 지침을 제공합니다. 예를 들어, 다른 계정에 대해 키를 사용했거나 Adobe Commerce 키 대신 Magento Open Source 키를 사용했을 수 있습니다.
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce on cloud: 인증 키 변경 및 재배포

이 문서에서는 다양한 인증 키를 사용하여 클라우드 인프라에 Adobe Commerce을 다시 배포하는 방법에 대한 지침을 제공합니다. 예를 들어, 다른 계정에 대해 키를 사용했거나 Adobe Commerce 키 대신 Magento Open Source 키를 사용했을 수 있습니다.

잘못된 키를 사용한 경우 배포가 실패합니다. 복구하려면 프로젝트를 복제하고 올바른 키를 `auth.json`을 누르고 변경 사항을 마스터 분기에 푸시합니다.

이 문서에서는 프로젝트에 `master` 분기만(`master` 는 처음 프로젝트를 만들 때 기본 분기입니다.

올바른 인증 키를 사용하여 재배포하려면 다음을 수행하십시오.

1. 클라우드 인프라의 Adobe Commerce SSH 키가 있는 컴퓨터에 로그인합니다.
1. 프로젝트에 로그인:

   ```
   magento-cloud login
   ```

1. 분기를 만들어 이름으로 코드를 업데이트합니다. `auth`:

   ```
   magento-cloud environment:branch auth master
   ```

1. 프로젝트 루트 디렉토리로 변경합니다.
1. 열기 `auth.json` 텍스트 편집기에서.

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. 올바른 인증 키를 추가합니다.
1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 변경 내용을 커밋하고 병합합니다.

   ```
   git add -A
   ```

   ```
   git commit -m "<description of change>"
   ```

   ```
   git push origin master
   ```

1. 배포가 완료될 때까지 기다립니다.

메시지가 배포가 성공했는지 여부를 나타냅니다. 다음 중 하나로 이동하여 성공적인 배포를 확인할 수 있습니다. **환경 경로** 화면에 표시됩니다.
