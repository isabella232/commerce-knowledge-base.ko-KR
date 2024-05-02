---
title: 빠른 체크아웃 문제 해결
description: 이 문서에서는 Adobe Commerce 확장에 대한 빠른 체크아웃 기능을 사용하는 동안 발생할 수 있는 문제에 대해 설명하고 확장을 성공적으로 사용할 수 있도록 이러한 문제를 해결하는 솔루션을 제공합니다.
exl-id: 8ab46318-d62a-4b7e-bbe5-4c52cfeb9e36
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# 빠른 체크아웃 문제 해결

이 문서에서는 Adobe Commerce 확장에 대한 빠른 체크아웃 기능을 사용하는 동안 발생할 수 있는 문제에 대해 설명하고 확장을 성공적으로 사용할 수 있도록 이러한 문제를 해결하는 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* 다음 [빠른 체크아웃](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/overview.html) 는 Magento Open Source 및 Adobe Commerce 모두와 호환됩니다. 다음을 참조하십시오 [수명 주기 정책](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) 를 참조하십시오.

## 잘못된 작성기 키 및 최소 안정성이에 `RC`

<u>원인</u>:

다음 오류 메시지가 표시되면 잘못된 작성기 키가 있는 것입니다.

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

<u>솔루션</u>:

작성기 키가 _MAGENTO ID_ 빠른 체크아웃 등록 중에 사용됩니다.

구성된 작성기 키를 보려면 다음을 수행하십시오.

1. 의 위치 찾기 `auth.json` 파일:

   ```bash
   composer config --global home
   ```

1. 보기 `auth.json` 파일:

   ```bash
   cat /path/to/auth.json
   ```

1. 다음을 참조하십시오 [Magento ID와 연결된 키](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

1. 최소 안정성을 다음으로 설정 `RC` 다음에서 `composer.json` 파일.

   ```json
   "minimum-stability": "RC"
   ```

## 메모리가 부족하여 PHP를 사용할 수 없습니다.

<u>원인</u>:

PHP에 대한 충분한 메모리가 없음을 나타내는 다음 오류 메시지가 표시됩니다.

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

<u>솔루션</u>:

[메모리 제한 늘리기](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) 의 환경에 있는 PHP용 `php.ini`.

또는 다음 명령을 사용하여 메모리 제한을 지정할 수 있습니다. `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

For example:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## 새 배송 주소로 상세 주소 라인 추가

빠른 체크아웃 확장에 대해 알려진 문제가 있습니다.

다음을 수행하는 경우 [bolt 계정으로 로그인](https://help.bolt.com/shoppers/guides/checkout/log-in/), 주소 당 4줄로 제한된 새 배송 주소를 추가할 수 있습니다.

새 배송 주소에 4줄 이상이 포함된 경우 저장되지 않습니다.

Adobe Commerce은 일반적으로 최대 20개의 상세 주소 라인을 지원하도록 구성할 수 있습니다.

## 다음의 예기치 않은 비헤이비어 `Display Billing Address On` 이(가) (으)로 설정됨 `payment page`

빠른 체크아웃 확장에 대해 알려진 문제가 있습니다.

다음을 설정하는 경우 `Display Billing Address On` 매개 변수를 `payment page` 및 [bolt 계정으로 로그인](https://help.bolt.com/shoppers/guides/checkout/log-in/) 을(를) 확인하면 `My billing and shipping address are the same` 확인란을 선택하면 라디오 버튼이 표시됩니다 `use existing card`. 청구 주소는 새 신용 카드에만 적용되므로 Bolt 사용자가 새 신용 카드 옵션을 추가할 때까지 주소가 표시되지 않습니다.

다음을 참조하십시오. [체크아웃](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 항목 을 참조하십시오 `Display Billing Address On` 매개 변수.
