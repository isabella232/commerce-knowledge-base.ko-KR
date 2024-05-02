---
title: 캐시된 이미지는 2.2.X에서 2.3.X로 업그레이드한 후 로드되지 않음
description: 이 문서에서는 클라우드 인프라 2.2.X의 Adobe Commerce에서 2.3.X로 업그레이드한 후 캐시된 이미지가 표시되지 않는 문제에 대한 해결 방법을 제공합니다.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# 캐시된 이미지는 2.2.X에서 2.3.X로 업그레이드한 후 로드되지 않음

이 문서에서는 클라우드 인프라 2.2.X의 Adobe Commerce에서 2.3.X로 업그레이드한 후 캐시된 이미지가 표시되지 않는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 버전 및 버전:

* Adobe Commerce on cloud infrastructure Pro 플랜 아키텍처 2.2.X, 2.3.X

## 문제

Adobe Commerce이 2.2.X에서 2.3.X로 업그레이드된 후 캐시된 제품 이미지를 사용할 수 없으며 대신 404 페이지가 표시됩니다.

이 문제는에 설정된 잘못된 Nginx 구성으로 인해 발생합니다. `.magento.app.yaml`: `index.php` (또는 없음)은 `"/media"` 대신 위치 `passthru: /get.php`.

## 솔루션

1. 다음을 확인: `.magento.app.yaml` 구성 파일, 위치 `"/media"` 위치. 올바른 구성은 다음과 같습니다.

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. If `passthru` 이(가) (으)로 설정되지 않음 `"/get.php"` 및 `expires` 가 설정되지 않은 경우 다음 단계를 수행하십시오.
1. 구성 파일을 수정합니다.
   * 스타터 플랜: 파일을 직접 수정하고 변경 사항을 푸시합니다.
   * Pro 플랜:
   * 통합: 파일을 직접 수정하고 변경 사항을 푸시합니다.
   * 스테이징 및 프로덕션: 파일을 직접 수정하고 변경 사항을 푸시한 다음 [Adobe Commerce 지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 적용.

1. 에 설명된 대로 Commerce 관리자에서 Fastly 이미지 최적화를 활성화합니다(Fastly는 이전에 구성해야 함). <https://devdocs.magento.com/guides/v2.3/cloud/cdn/fastly-image-optimization.html>.

구성이 올바르지만 문제가 계속 발생하면 조사를 계속하거나 [Adobe Commerce 지원](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
