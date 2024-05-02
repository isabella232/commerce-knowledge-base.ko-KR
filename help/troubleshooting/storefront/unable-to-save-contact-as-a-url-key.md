---
title: '*contact*를 URL 키로 저장할 수 없음'
description: '이 문서에서는 *contact*를 제품 또는 CMS 페이지의 URL 키(예: "/contact")로 저장할 수 없는 문제에 대한 해결 방법을 제공합니다. URL 키를 저장하려고 하면 URL 키가 중복 URL임을 나타내는 오류가 표시됩니다.'
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 저장할 수 없음 *연락처* URL 키로 사용

이 문서에서는 을(를) 저장할 수 없는 문제에 대한 해결 방법을 제공합니다 *연락처* 제품 또는 CMS 페이지의 URL 키(예: &quot;/contact&quot;)로.

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 메서드) 2.4.x

## 문제

용어를 사용하여 제품 또는 CMS 페이지를 저장할 수 없습니다 *연락처* URL 키로 사용됩니다. URL 키를 저장하려고 하면 URL 키가 중복 URL임을 나타내는 오류가 표시됩니다.

<u>재현 단계</u>:

다음을 사용하여 CMS 페이지 만들기 *연락처* URL 키로 사용됩니다.

<u>예상 결과</u>:

페이지가 다음으로 저장됨 *연락처* URL 키로 사용됩니다.

<u>실제 결과</u>:

페이지를 저장할 수 없습니다. 다음과 같은 오류가 발생합니다. *URL 키 필드에 지정된 값은 이미 존재하는 URL을 생성합니다.*

## 원인

*연락처* 은(는)에 정의된 예약어입니다. `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## 솔루션

이 용어를 사용할 수 없습니다. *연락처* 그러나 URL 키로 이 용어를 사용할 수 있습니다 *연락처* 다른 문자 또는 숫자와 결합됨(예: *contact1* 및 *contact2*). 이 용어는 반드시 다음과 같을 필요는 없습니다. *연락처+\&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;>*&#x200B;에서 용어는 길이가 255자를 초과하지 않는 한 어떤 문자열이든 사용할 수 있습니다.

다음 단계를 수행하십시오.

1. Commerce 관리자에 로그인합니다.
1. 다음으로 이동 **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. 클릭 **[!UICONTROL Add URL Rewrite]**.
1. 선택 *[!UICONTROL Custom]* 다음에 있음 [!UICONTROL Create URL Rewrite] 드롭다운.
   1. 다음에서 [!UICONTROL Request Path], &quot;contact&quot;를 입력합니다. 다음 사항에 주의하십시오. [!UICONTROL Request Path] 는 사용자가 브라우저에 입력하는 항목이고 [!UICONTROL Target Path] 은 로 리디렉션해야 하는 위치입니다.
   1. 다음에서 [!UICONTROL Target Path]새 URL 키를 입력합니다(예: &quot;contact1&quot;).
   1. 선택 *[!UICONTROL No]* 다음에서 [!UICONTROL Redirect] 드롭다운.

## 관련 읽기

* [URL 재작성](https://docs.magento.com/user-guide/marketing/url-rewrite.html) 사용 안내서에서 참조하십시오.
* [SEO 우수 사례](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) 사용 안내서에서 참조하십시오.
