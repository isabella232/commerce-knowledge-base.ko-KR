---
title: '"shipping"을 URL 키로 저장할 수 없음'
description: '이 문서에서는 "배송"을 제품 또는 CMS 페이지의 URL 키(예: "/shipping")로 저장할 수 없는 문제에 대한 해결 방법을 제공합니다. URL 키를 저장하려고 하면 URL 키가 중복 URL임을 나타내는 오류가 표시됩니다.'
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# &quot;shipping&quot;을 URL 키로 저장할 수 없음

이 문서에서는 &quot;배송&quot;을 제품 또는 CMS 페이지의 URL 키(예: &quot;/shipping&quot;)로 저장할 수 없는 문제에 대한 해결 방법을 제공합니다. URL 키를 저장하려고 하면 URL 키가 중복 URL임을 나타내는 오류가 표시됩니다.

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 메서드) 2.4.x

## 문제

URL 키에 &quot;shipping&quot;이라는 용어가 있는 CMS 페이지를 저장할 수 없습니다.

<u>재현 단계</u>:

URL 키를 &quot;shipping&quot;으로 사용하는 CMS 페이지를 만듭니다.

<u>예상 결과</u>:

페이지가 URL 키에 &quot;shipping&quot;과 함께 저장됩니다.

<u>실제 결과</u>:

저장할 수 없으며 오류가 나타납니다. *URL 키 필드에 지정된 값은 이미 존재하는 URL을 생성합니다.*

## 원인

배송은 다음에 정의된 예약어입니다. `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## 솔루션

URL 키에는 &quot;shipping&quot;이라는 용어를 사용할 수 없습니다. 그러나 다른 문자나 번호와 함께 &quot;shipping&quot;이라는 용어를 사용할 수 있습니다(예: &quot;shipping1&quot; 및 &quot;shipping2&quot;). 용어가 &quot;shipping&quot;+일 필요는 없습니다&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - 길이가 255자를 초과하지 않는 한 용어는 어떤 문자열이든 될 수 있습니다.

다음 단계를 수행하십시오.

1. Commerce 관리자에 로그인합니다.
1. 다음으로 이동 **마케팅** > SEO 및 검색 > **URL 재작성**.
1. 클릭 **URL 재작성 추가**.
1. 선택 *사용자 정의* URL 재작성 만들기 드롭다운에서 을 참조하십시오.
   1. 요청 경로 &quot;shipping&quot;을 입력합니다. 참고: 요청 경로는 사용자가 브라우저에 입력하는 위치이며 대상 경로는 리디렉션해야 하는 위치입니다.
   1. 대상 경로에 새 URL 키(예: &quot;shipping1&quot;)를 입력합니다.
   1. 선택 **아니요** 리디렉션 드롭다운에서 을 클릭합니다.

## 관련 읽기

* [URL 재작성](https://docs.magento.com/user-guide/marketing/url-rewrite.html) 사용 안내서에서 참조하십시오.
* [SEO 우수 사례](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) 사용 안내서에서 참조하십시오.
