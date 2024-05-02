---
title: "[!DNL Fastly] 원본 클로킹 지원 FAQ"
description: 이 FAQ에서는 다음에 대한 일반적인 질문에 대해 설명합니다. [!DNL Fastly] Adobe Commerce(2021년부터 완전히 구현됨)의 원본 클로킹 지원.
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 348a1f6e455aff9ad7c562ea20c95f27c9ee0b86
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# [!DNL Fastly] 원본 차단 사용 FAQ

이 FAQ에서는 다음에 대한 일반적인 질문에 대해 설명합니다. [!DNL Fastly] Adobe Commerce(2021년부터 완전히 구현됨)의 원본 클로킹 지원.

## 이란? [!DNL Fastly] 원본 클로킹?

원본 차단은 클라우드 인프라의 Adobe Commerce에서 다음을 차단할 수 있는 보안 기능입니다. [!DNL non-Fastly] 트래픽(DDoS 공격을 방지하기 위해 클라우드 인프라(원본)로 이동).

## Origin Cloaking의 이점은 무엇입니까?

원본 클로킹은 트래픽이 [!DNL Fastly Web Application Firewall] (WAF) 및 엄격하게 정의된 플로우 **[!DNL Fastly]** > **로드 밸런서** > **인스턴스**. 이 구현으로 모든 트래픽은 [!DNL Fastly] 로드 밸런서에 내장된 내부 WAF 및 WAF.

## 이 원본 차단 활성화가 발생하는 이유는 무엇입니까?

이 기능은 원래 클라우드 인프라에서 Adobe Commerce의 이점을 활용하기 위해 만들어졌습니다.

## 내 프로젝트에 대해 원본 차단 활성화를 요청해야 합니까?

아니. 이 기능은 모든 클라우드 프로젝트에서 이미 구현했어야 하며, 2021년 이후 프로비저닝된 모든 프로젝트는 기본적으로 이를 활성화했을 것입니다. 그러나 다음 방법으로 프로젝트에 대해 원천 숨김을 비활성화하도록 요청할 수 있습니다. [지원 요청 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 원본 클로킹이 보내는 IP 주소를 변경합니까?

아니, 그렇지 않아

## 원본 클로킹이 REST API에 영향을 줍니까?

[!DNL Fastly] 는 API 호출을 캐시하지 않으므로 클라이언트는 변경 사항이 적합해야 합니다. 원본 클로킹은 다음과 같이 원본으로 직접 이동하는 요청만 차단합니다.

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

이 예에서 URL을 로 변경하면 클라이언트는 여전히 API를 히트할 수 있습니다. ``mywebsite.com``:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## 이러한 변경 사항이 배포 및 다운타임에 영향을 미칩니까?

아니요, 이 변경 사항은 **아님** 배포와 다운타임에 영향을 미칩니다.

## 프로젝트에 여러 스테이징 환경이 있는 경우 원본 클로킹이 모든 스테이징 환경에 적용됩니까?

예. 프로젝트에 여러 스테이징 환경이 있는 경우 변경 사항이 모든 스테이징 환경에 적용됩니다.
