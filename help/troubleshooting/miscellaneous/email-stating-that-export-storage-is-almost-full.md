---
title: '내보내기 저장소가 거의 꽉 찼음을 알리는 이메일'
description: 이 문서에서는 내보내기 저장소가 거의 가득 찼다는 내용의 이메일을 받는 문제에 대한 해결 방법을 제공합니다.
feature: Cloud, Storage, Media
role: Developer
source-git-commit: 8f783cb4245911bded5e9946917e2f2c3e78a705
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 내보내기 저장소가 거의 꽉 찼다는 이메일

이 문서에서는 내보내기 저장소가 거의 가득 찼다는 내용의 이메일을 받는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce(모든 버전)

## 문제

다음 콘텐츠가 포함된 이메일을 받았지만 을(를) 찾을 수 없습니다. *내보내기* 폴더:

*클러스터 XXX의 &#39;내보내기&#39; 스토리지가 약 &#39;85%&#39; 꽉 찼습니다.*
*필요한 경우 사용을 검토하거나 청소를 수행하거나 업사이징을 요청하십시오.*
*또한 스토리지가 중요 임계값 수준에 도달하면 자동으로 업사이징을 시도합니다.*

## 원인

이메일은 다음을 참조합니다. **내보내기** 스토리지: 파일/미디어에 할당된 디스크 양이며 이름이 인 특정 폴더가 아닙니다. *내보내기*.

## 솔루션

환경에서 파일 사용을 검토해야 합니다. 이 명령을 실행하여 기존 사용량을 가져옵니다.

`df -h |grep data`

파일 스토리지가 채워지는 일반적인 위치는 다음과 같습니다. *pub/media/catalog/product/cache* 또는 *var/log* 개 폴더. 파일에서 사용하는 디스크 공간을 확인하려면 적절한 경로를 사용하여 이 명령을 실행합니다 */path/to/folder*:

`du -shc` */path/to/folder*

미디어 디스크 사용량이 전체 디스크 공간의 큰 부분을 차지하는 경우 [Fastly Deep 이미지 최적화](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization)을 클릭한 다음 *pub/media/catalog/product/cache* 폴더를 서버에 수동으로 생성합니다.

## 관련 읽기

[전용 클러스터 확인](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) 을 참조하십시오.