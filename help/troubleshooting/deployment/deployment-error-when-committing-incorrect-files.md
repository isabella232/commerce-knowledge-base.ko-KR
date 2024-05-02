---
title: 잘못된 파일을 커밋할 때 배포 오류 발생
description: 이 문서에서는 추가해서는 안 되는 파일/폴더 저장소에 대한 잘못된 커밋으로 인해 배포 오류가 발생하는 문제에 대한 해결 방법을 제공합니다.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# 잘못된 파일을 커밋할 때 배포 오류 발생

이 문서에서는 추가해서는 안 되는 파일/폴더 저장소에 대한 잘못된 커밋으로 인해 배포 오류가 발생하는 문제를 해결할 수 있습니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce(모든 버전)

## 문제

파일/폴더 저장소에 커밋할 때 배포 오류가 발생합니다. 예를 들어, 다음 오류는 현재 DB를 사용할 수 없을 때 DB에 연결하려고 시도했기 때문에 발생합니다. [빌드 단계](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#build-phase):

```SQL
SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          PDO::__construct(): php_network_getaddresses: getaddrinfo for database.inte  
          rnal failed: Name or service not known       
```

## 원인

특정 파일/폴더는 히트를 발생시키므로 저장소에 커밋해서는 안 됩니다. [배포 워크플로](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html).

## 솔루션

다음 파일/폴더가 있는 경우 저장소에서 해당 파일/폴더를 제거합니다.

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
