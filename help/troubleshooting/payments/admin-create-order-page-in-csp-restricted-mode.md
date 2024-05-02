---
title: 에서 주문 만들기 페이지 문제 해결 [!UICONTROL CSP] 제한된 모드
description: 이 문서에서는 CSP 제한 모드가 활성화되면 관리자 측에서 주문을 생성하는 오류에 대해 설명하고 이러한 오류를 수정하는 솔루션을 제공합니다.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# 에서 주문 만들기 페이지 문제 해결 [!UICONTROL CSP] 제한된 모드

이 문서에서는 를 사용하여 관리자 측에서 주문을 작성하는 동안의 Adobe Commerce 2.4.7 문제에 대한 설명 및 수정 사항을 제공합니다. **[!UICONTROL CSP restricted mode]** 은(는) *활성화됨*, &quot; 사용&#x200B;*다음 콘텐츠 보안 정책 지시문을 위반하므로 인라인 스크립트 실행을 거부했습니다. &quot;script-src ...*&quot; 브라우저 콘솔 로그에 오류 메시지가 표시됩니다.

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure, Adobe Commerce 온프레미스 및 Magento Open Source:

* 2.4.7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## 문제 - 관리자 **주문 만들기** 페이지가 손상되었거나 로드할 수 없습니다.

관리자 **주문 만들기** 페이지가 손상되었거나 로드할 수 없습니다.*다음 콘텐츠 보안 정책 지시문을 위반하므로 인라인 스크립트 실행을 거부했습니다. &quot;script-src ...*&quot; 브라우저 콘솔 로그에 오류 메시지가 표시됩니다.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. 새 주문을 만듭니다.

<u>예상 결과</u>:

관리자 **주문 만들기** 페이지가 정상적으로 완전히 로드됩니다.

<u>실제 결과</u>:

관리자 **주문 만들기** 페이지가 비어 있거나 구성 요소가 없습니다. 다음 [!DNL JS] 브라우저 콘솔 로그에 오류가 표시됩니다.&quot;*다음 콘텐츠 보안 정책 지시문을 위반하므로 인라인 스크립트 실행을 거부했습니다. &quot;script-src ...*&quot;

### 원인

Adobe Commerce 및 Magento Open Source 버전 2.4.7 이상에서는 **[!UICONTROL CSP]** 다음에서 구성됨: `restrict-mode`, 기본적으로 상점 및 관리 영역, 의 결제 페이지에 대해 `report-only` 다른 모든 페이지의 모드.
해당 **[!UICONTROL CSP]** 헤더에 다음 항목이 포함되지 않음 `unsafe-inline` 키워드 내부 `script-src` 지급 페이지에 대한 지시문입니다. 또한, [!DNL whitelisted] 인라인 스크립트가 허용됩니다.

### 솔루션

특정 스크립트가 다음 이유로 차단되어 사용자에게 브라우저 오류가 표시될 수 있습니다 [!UICONTROL CSP]:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>이 문제를 해결하려면 다음 중 하나를 수행해야 합니다</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) 을(를) 사용하는 차단된 스크립트 `SecureHtmlRenderer` 클래스.
1. 사용 `CSPNonceProvider` 스크립트를 실행할 수 있도록 해 주는 클래스입니다.
Adobe Commerce 및 Magento Open Source 2.4.7 이상에는 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 고유한 생성을 용이하게 하는 공급자 [!DNL nonce] 각 요청에 대한 문자열입니다. 다음 [!DNL nonce] 그러면 문자열이 [!UICONTROL CSP] 머리글입니다.

   사용 `generateNonce` 의 함수 `Magento\Csp\Helper\CspNonceProvider` 을(를) 가져오려면 [!DNL nonce] 문자열.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [추가 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) 모듈에 `csp_whitelist.xml` 파일.

## 문제 - 결제 방법이 없거나 작동하지 않음

결제 방법이 누락되었거나 관리자에서 작동하지 않습니다. **페이지 주문 만들기**, &quot; 사용&#x200B;*다음 콘텐츠 보안 정책 지시문을 위반하므로 인라인 스크립트 실행을 거부했습니다. &quot;script-src ...*&quot; 브라우저 콘솔 로그에 오류 메시지가 표시됩니다.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. 새 주문을 만듭니다.
1. 새 고객을 만듭니다.
1. 고객 세부 정보를 입력합니다.
1. 주문 상세내역(제품, 운송 방법)을 입력합니다.
1. 결제 방법을 선택합니다.

<u>예상 결과</u>:

결제 방법을 선택하고 주문을 진행할 수 있습니다.

<u>실제 결과</u>:

결제 방법이 없거나 작동하지 않습니다. 다음 [!DNL JS] 브라우저 콘솔 로그에 오류가 표시됩니다.&quot;*다음 콘텐츠 보안 정책 지시문을 위반하므로 인라인 스크립트 실행을 거부했습니다. &quot;script-src ...*&quot;.

### 원인

Adobe Commerce 및 Magento Open Source 버전 2.4.7 이상에서는 **[!UICONTROL CSP]** 다음에서 구성됨: `restrict-mode`, 기본적으로 상점 및 관리 영역, 의 결제 페이지에 대해 `report-only` 다른 모든 페이지의 모드.
해당 **[!UICONTROL CSP]** 헤더에 다음 항목이 포함되지 않음 `unsafe-inline` 키워드 내부 `script-src` 지급 페이지에 대한 지시문입니다. 또한, [!DNL whitelisted] 인라인 스크립트가 허용됩니다.

### 솔루션

특정 스크립트가 다음 이유로 차단되어 사용자에게 브라우저 오류가 표시될 수 있습니다 **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>이 문제를 해결하려면 다음 중 하나를 수행해야 합니다</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) 을(를) 사용하는 차단된 스크립트 `SecureHtmlRenderer` 클래스.
1. 사용 `CSPNonceProvider` 스크립트를 실행할 수 있도록 해 주는 클래스입니다.
Adobe Commerce 및 Magento Open Source 2.4.7 이상에는 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 고유한 생성을 용이하게 하는 공급자 [!DNL nonce] 각 요청에 대한 문자열입니다. 다음 [!DNL nonce] 그러면 문자열이 [!UICONTROL CSP] 머리글입니다.

   사용 `generateNonce` 의 함수 `Magento\Csp\Helper\CspNonceProvider` 을(를) 가져오려면 [!DNL nonce] 문자열.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [추가 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) 모듈에 `csp_whitelist.xml` 파일.

## 문제 - 관리자가 주문할 수 없음

관리자가 책임자에 대한 주문을 제출할 수 없음 **주문 페이지 만들기**, &quot; 사용&#x200B;*다음 콘텐츠 보안 정책 지시문을 위반하므로 인라인 스크립트 실행을 거부했습니다. &quot;script-src ...*&quot; 브라우저 콘솔 로그에 오류 메시지가 표시됩니다.

<u>재현 단계</u>:

1. 다음으로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. 새 주문을 만듭니다.
1. 새 고객을 만듭니다.
1. 고객 세부 정보를 입력합니다.
1. 주문 상세내역(제품, 운송 방법)을 입력합니다.
1. 결제 방법을 선택합니다.
1. 주문을 제출합니다.

<u>예상 결과</u>:

주문을 정상적으로 제출할 수 있습니다.

<u>실제 결과</u>:

주문을 제출할 수 없습니다. 다음 [!DNL JS] 브라우저 콘솔 로그에 오류가 표시됩니다.&quot;*다음 콘텐츠 보안 정책 지시문을 위반하므로 인라인 스크립트 실행을 거부했습니다. &quot;script-src ...*&quot;

### 원인

Adobe Commerce 및 Magento Open Source 버전 2.4.7 이상에서는 **[!UICONTROL CSP]** 다음에서 구성됨: `restrict-mode`, 기본적으로 상점 및 관리 영역, 의 결제 페이지에 대해 `report-only` 다른 모든 페이지의 모드.
해당 **[!UICONTROL CSP]** 헤더에 다음 항목이 포함되지 않음 `unsafe-inline` 키워드 내부 `script-src` 지급 페이지에 대한 지시문입니다. 또한, [!DNL whitelisted] 인라인 스크립트가 허용됩니다.

### 솔루션

특정 스크립트가 다음 이유로 차단되어 사용자에게 브라우저 오류가 표시될 수 있습니다 **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>이 문제를 해결하려면 다음 중 하나를 수행해야 합니다</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) 을(를) 사용하는 차단된 스크립트 `SecureHtmlRenderer` 클래스.
1. 사용 `CSPNonceProvider` 스크립트를 실행할 수 있도록 해 주는 클래스입니다.
Adobe Commerce 및 Magento Open Source 2.4.7 이상에는 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 고유한 생성을 용이하게 하는 공급자 [!DNL nonce] 각 요청에 대한 문자열입니다. 다음 [!DNL nonce] 그러면 문자열이 [!UICONTROL CSP] 머리글입니다.

   사용 `generateNonce` 의 함수 `Magento\Csp\Helper\CspNonceProvider` 을(를) 가져오려면 [!DNL nonce] 문자열.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [추가 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) 모듈에 `csp_whitelist.xml` 파일.
