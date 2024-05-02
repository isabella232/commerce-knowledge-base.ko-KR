---
title: PHP 설정 오류
description: 이 문서에서는 PHP 설정 오류에 대한 해결책을 제공합니다.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# PHP 설정 오류

이 문서에서는 PHP 설정 오류에 대한 해결책을 제공합니다.

## PHP 메모리 제한 오류

준비 검사를 통해 PHP 프로세스에 1GB 이상의 메모리가 할당되어 있는지 확인합니다. 이 설정은 선택적 샘플 데이터 설치를 포함하여 대부분의 설치에 충분해야 합니다. 단, 디버깅에는 최소 2GB를 사용하는 것이 좋습니다.

PHP 메모리 제한을 늘리려면:

1. Adobe Commerce 서버에 로그인.
1. 다음 위치 찾기 `php.ini` 다음 명령을 사용한 파일:

   ```
   bash    $ php --ini
   ```

1. 을 사용하는 사용자로서 `root` 권한, 텍스트 편집기를 사용하여 `php.ini` 지정한 사람: `Loaded Configuration File`.
1. 찾기 `memory_limit`.
1. 값으로 변경 `2GB` 일반적인 사용 및 디버깅에 사용됩니다.
1. 변경 내용 저장 `php.ini` 텍스트 편집기를 종료합니다.
1. 웹 서버를 다시 시작합니다. 예제는 다음과 같습니다.

   * CentOS: `service httpd restart`
   * 우분투: `service apache2 restart`
   * nginx (CentOS 및 Ubuntu 모두): `service nginx restart`

1. 설치를 다시 시도하십시오.

## 큰 양식으로 인한 max-input-vars 오류

많은 스토뷰, 제품, 속성 또는 옵션이 있는 구성은 사전 설정된 PHP 제한을 초과하는 양식을 생성할 수 있습니다. 전송된 값 수가 `max-input-vars` 한도 이내 설정 `php.ini` (기본값은 1000), 나머지 데이터는 전송되지 않고 해당 데이터베이스 값이 업데이트되지 않습니다. 이 경우 PHP 로그에 경고가 나타납니다.

```terminal
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

에 대한 &#39;적절한&#39; 값이 없습니다. `max-input-vars`: 구성의 크기와 복잡성에 따라 다릅니다. 에서 값 수정 `php.ini` 필요에 따라 파일을 생성합니다. 다음을 참조하십시오 [필수 PHP 설정](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).

## xdebug 최대 함수 중첩 수준 오류

다음을 참조하십시오 [설치하는 동안 xdebug 최대 함수 중첩 수준 오류](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## PHTML 템플릿에 액세스할 때 오류가 표시됩니다

오류 텍스트는 일반적으로 다음과 같습니다.

```terminal
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### 해결 방법: 설정 `asp_tags = off` php.ini에서

여러 템플릿에는 포함된 템플릿(Twig와 같은 다양한 템플릿 엔진 사용)에 대한 지원 추상 수준에 대한 구문이 있습니다. `<% %>` 태그, 예: [템플릿](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) 제품 이미지를 표시하는 경우:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

다음에 대한 추가 정보: [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

편집 `php.ini` 및 설정 `asp_tags = off`. 자세한 내용은 [필수 PHP 설정](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).
