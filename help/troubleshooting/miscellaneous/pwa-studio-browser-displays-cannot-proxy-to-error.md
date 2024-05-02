---
title: 'PWA Studio: 브라우저에 "프록시 대상 불가" 오류 표시'
description: 이 항목에서는 웹 브라우저에 "*프록시 대상*"이 표시되고 콘솔에
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# PWA Studio: 브라우저에 &quot;프록시 대상 불가&quot; 오류 표시

이 항목에서는 웹 브라우저에 &quot;*에 프록시를 지정할 수 없음*&quot;콘솔에는

```
ENOTFOUND
```

Adobe Commerce용 점진적 웹 앱(PWA) Studio를 사용할 때 오류가 발생했습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce PWA Studio

## 문제

<u>재현할 단계</u>:

* 브라우저에 Adobe Commerce 스토어를 로드합니다.

<u>예상 결과</u>:

* Adobe Commerce 저장소는 정상적으로 브라우저에 로드됩니다.

<u>실제 결과</u>:

* 웹 브라우저에 &quot;*에 프록시를 지정할 수 없음*&quot;오류이며 콘솔에는 다음과 같은 오류가 표시됩니다.

```
    ENOTFOUND
```


## 원인

NodeJS가 Adobe Commerce 저장소의 호스트 이름을 확인할 수 없습니다.

## 솔루션

1. Adobe Commerce 스토어가 둘 이상의 웹 브라우저에 로드되는지 확인하십시오.
1. 로컬 DNS 서버 또는 VPN을 실행 중인 경우 호스트 파일( 위치: `/etc/hosts`) 이 도메인을 수동으로 매핑([호스트 파일 편집에 대한 일반 지침](https://linuxize.com/post/how-to-edit-your-hosts-file/))를 클릭하여 NodeJS로 확인할 수 있습니다.

## 관련 읽기

* [Adobe Commerce 설명서 PWA Studio](https://magento.github.io/pwa-studio/)
* [도구 및 라이브러리](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
