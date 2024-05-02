---
title: PayPal 샌드박스 계정이 확인되지 않음
description: 이 문서에서는 결제 서비스에 대한 PayPal 샌드박스 계정이 확인되지 않아 샌드박스 온보딩을 완료할 수 없는 이유를 설명합니다.
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# PayPal 샌드박스 계정이 확인되지 않음

이 문서에서는 결제 서비스에 대한 PayPal 샌드박스 계정이 확인되지 않아 샌드박스 온보딩을 완료할 수 없는 이유를 설명합니다.

## 영향을 받는 제품 및 버전

* [결제 서비스](https://marketplace.magento.com/magento-payment-services.html) 는 이제 Adobe Commerce 버전 2.4.0에서 2.4.4로 호환됩니다.

## 문제

당사 [온보딩 설명서](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) 에서는 PayPal 계정에 등록하고 PayPal Developers 계정에 로그인한 다음 샌드박스 계정을 만들도록 지시합니다. PayPal 온보딩 팝업 창에서 온보딩 중에 새 계정을 만들도록 선택하면 PayPal에서 샌드박스 계정을 확인할 수 없고 온보딩을 완료할 수 없습니다.

<u>재현 단계</u>:

1. 본인 [결제 서비스 설치](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) 및 [Commerce 서비스 구성](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. 다음으로 이동 **결제 서비스** 관리자 및 [샌드박스 온보딩 시작](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. 표시되는 PayPal 온보딩 팝업에서 (대신) 새 비즈니스 계정을 만듭니다. [이전에 만든 PayPal 샌드박스 계정으로 로그인](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) 온보딩 중.
1. PayPal 온보딩을 완료했습니다.
1. 샌드박스 결제가 보류 중이며 온보딩을 완료하려면 PayPal로 이메일 주소를 확인해야 한다는 알림이 관리자에 표시됩니다.

   PayPal에서 이메일 주소를 확인할 수 없어 확인 이메일을 받지 못했습니다.

## 원인

PayPal 계정 이전에 샌드박스 계정을 만들면 PayPal에서 샌드박스 계정을 확인할 수 없으며 샌드박스 온보딩을 완료할 수 없습니다(결제를 승인하거나 샌드박스 모드를 테스트할 수 없음).

## 솔루션

1. 에서 생성된 샌드박스 계정 사용 [PayPal 개발자](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) 포털.
1. 클릭 [샌드박스 재설정](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) 샌드박스 온보딩을 다시 시작하십시오.
1. [지원 문의](mailto:payment-services-support@adobe.com) 계정 문제를 완화할 수 없는 경우 온보딩을 재개하고 지불을 수락할 수 있습니다.
