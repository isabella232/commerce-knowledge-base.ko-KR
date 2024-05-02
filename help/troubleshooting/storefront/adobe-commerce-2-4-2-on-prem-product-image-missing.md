---
title: 'Adobe Commerce 온-프레미스 2.4.2: 제품 이미지 누락'
description: 이 문서에서는 제품 이미지가 제품 페이지에 업로드되지 않는 알려진 Adobe Commerce 온-프레미스 2.4.2 문제에 대해 설명합니다. 이 문제는 버전 2.4.3 이후의 향후 버전에서 해결될 예정입니다. 지금은 사용할 수 있는 솔루션이 없지만 해결 방법으로 Nginx를 비활성화하여 이미지 크기를 조정할 수 있습니다.
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce 온-프레미스 2.4.2: 제품 이미지 누락

이 문서에서는 제품 이미지가 제품 페이지에 업로드되지 않는 알려진 Adobe Commerce 온-프레미스 2.4.2 문제에 대해 설명합니다. 이 문제는 버전 2.4.3 이후의 향후 버전에서 해결될 예정입니다. 지금은 사용할 수 있는 솔루션이 없지만 해결 방법으로 Nginx를 비활성화하여 이미지 크기를 조정할 수 있습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.2

## 문제

제품 이미지가 `s3` 버킷이지만 다시 동기화되지 않습니다. `pub/media` 디렉토리. 이 문제는 다음 두 가지를 모두 사용할 때만 발생합니다.

* 이미지 크기를 조정할 수 있는 사이트 활성화 Nginx
* AWS `s3` 미디어 스토리지로

<u>전제 조건</u>:

Adobe Commerce이 Nginx와 함께 설치되었습니다.

<u>재현 단계</u>:

1. AWS을 사용하도록 Adobe Commerce 구성 `s3` 미디어 스토리지로 사용됩니다.
1. 다음을 사용하여 Nginx 구성 `nginx.conf.sample` Adobe Commerce 설치 디렉터리 및 Nginx 가상 호스트에 제공된 구성 파일입니다. 다음을 참조하십시오 [Nginx 구성](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/nginx.html#configure-nginx-ubuntu) 개발자 설명서에서 확인할 수 있습니다.
1. 하나의 제품 이미지로 간단한 제품을 만듭니다.
1. Nginx에는 이미지 크기 조정을 위한 주석 처리 없는 구성이 있습니다. `nginx.conf.sample` 다음과 비슷합니다.

```conf
load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
location /media/ {
    location ~* ^/media/catalog/.* {
        set $width "-";
        set $height "-";
        if ($arg_width != '') {
            set $width $arg_width;
        }
        if ($arg_height != '') {
            set $height $arg_height;
        }
        image_filter resize $width $height;
        image_filter_jpeg_quality 90;
    }
```

<u>예상 결과</u>:

제품 이미지가 제품 페이지에 업로드됩니다.

<u>실제 결과</u>:

제품 이미지가 제품 페이지에 업로드되지 않습니다.

## 해결 방법

이미지 크기를 조정하려면 Nginx를 비활성화하십시오.
