---
title: 모든 Adobe Commerce 버전에서 Google 맵 액세스 손실에 대한 패치를 수정했습니다.
description: '이 문서는 최근 항목과 호환되지 않는 Adobe Commerce 판매자에 대한 수정 사항을 제공합니다. [!DNL Google Maps] 버전: 3.54+.'
feature: Install, Upgrade
role: Developer
source-git-commit: 49bc0b643c10c6597d6a905935c36251e92b18f9
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# 수정된 패치 [!DNL Google Maps] 모든 Adobe Commerce 버전에서 액세스 손실

이 문서에서는 최근 버전과 호환되지 않는 Adobe Commerce 가맹점에 대한 수정 사항을 제공합니다 [!DNL Google Maps] 버전 3.54 이상. 이 수정 사항은 Adobe Commerce 판매자가 액세스할 수 없는 문제를 해결하기 위한 것입니다 [!DNL Google Maps] 더 이상 Adobe Commerce의 모든 버전에서 사용할 수 없습니다.

## 영향을 받는 버전 및 제품

* Adobe Commerce 및/또는 기타 사용된 기술의 버전.
* Adobe Commerce *2.4.4* - *2.4.7* on Cloud 및 온프레미스 버전.

## 문제

날짜 *2024년 6월 14일* [!DNL Google Maps] 버전 *3.53* 수명 종료에 도달했으며에 의해 꺼져 있음 [!DNL Google].

자세한 내용은 [[!DNL Google Maps] 플랫폼: JavaScript API](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions)를 매핑합니다.

Adobe Commerce은 최신 버전과 호환되지 않습니다. [!DNL  Google Maps] 버전 3.54 이상.

비호환성은 레거시로 인해 발생했습니다 `prototype.js script`, 다음을 통해 로드됨 `lib/web/legacy-build.min.js` 네이티브 Array.from 함수를 재정의하여 이 함수를 재정의하면 다음과 직접 충돌이 발생합니다. [!DNL  Google Maps] API.

참조: [[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices).

<u>재현 단계</u> :

1. 다음으로 이동 **[!UICONTROL Content]** > **[!UICONTROL Pages]** > 을(를) 클릭하고 **[!UICONTROL New Page]**.
1. 콘텐츠 블록을 확장하고 편집 을 클릭합니다. **[!DNL PageBuilder]** 단추를 클릭합니다.
1. 에서 맵 콘텐츠 블록을 드래그합니다. **[!DNL PageBuilder]** 메뉴를 페이지에 추가합니다.

<u>예상 결과:</u>

[!DNL Google Maps] 예상대로 작동해야 합니다.

<u> 실제 결과:</u>

에서 맵 콘텐츠 블록을 삭제할 때 **[!DNL PageBuilder]** 페이지를 표시하는 메뉴, 다음과 같은 오류 메시지 *&quot;죄송합니다. 문제가 발생했습니다.&quot;* 이 표시됩니다.

## 솔루션

* 패치 버전 2.4.4, 2.4.5, 2.4.6 또는 2.2.7의 모든 판매자는 해당 패치를 해당 버전에 적용해야 합니다.

## 패치

Adobe Commerce 버전에 따라 다음과 같은 첨부 패치를 사용합니다.

**버전 2.4.4의 경우**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**버전 2.4.5의 경우**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**버전 2.4.6의 경우**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**버전 2.4.7의 경우**
[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**참고 사항**

이 문제는 8월 보안 전용 패치 릴리스(2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10)의 범위에서 영구적으로 수정됩니다

## 관련 읽기

[Adobe에서 제공하는 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)