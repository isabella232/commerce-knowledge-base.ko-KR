---
title: 클라우드 인프라에서 VAT 번호(Adobe Commerce)를 확인할 수 없음
description: 이 문서에서는 VAT 번호 확인 중에 오류가 발생하는 문제에 대한 패치를 제공합니다.
exl-id: 9868e888-bad8-4823-acab-4b3804933cb0
feature: Cloud, Customer Service, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 클라우드 인프라에서 VAT 번호(Adobe Commerce)를 확인할 수 없음

이 문서에서는 VAT 번호 확인 중에 오류가 발생하는 문제에 대한 패치를 제공합니다.

## 영향을 받는 제품 및 버전

이미 릴리스된 p1 및 p2 버전을 포함하여 최대 2.3.6(2.3.5-p1 포함)의 모든 Adobe Commerce 온-프레미스 및 Adobe Commerce 온 클라우드 인프라 버전이 영향을 받았습니다. 여기에는 다음이 포함됩니다.

* 2.3.5-p1
* 2.3.5
* 2.3.4 - 2.3.4-p2
* 2.3.3 - 2.3.3-p1
* 2.3.2 -2.3.2-p2
* 2.0.0 - 2.3.1

## 문제

<u>재현 단계:</u>

1. 다음으로 이동 **스토어** > **구성** > **고객** > **고객 구성** > **새 계정 만들기 옵션** 및 설정 **자동 할당 활성화** 끝 **고객 그룹** 끝 *예*.
1. 다음으로 이동 **일반** > **정보 저장** > 을(를) 클릭하고 유효한 국가 및 VAT 번호를 설정합니다.
1. 클릭 **VAT 번호 유효성 검사**.

<u>예상 결과:</u>

유효성 검사가 완료되었습니다.

<u>실제 결과:</u>

다음 오류가 표시됩니다.&quot;*VAT 번호 확인 도중 오류 발생.*&quot;

## 솔루션

적용 [patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip) 이 문서에서 제공됩니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-27623\_EE\_2.3.2-p2\_COMPOSER\_v1.patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)

## 패치 적용 방법

다음을 참조하십시오 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 설명서를 참조하십시오.

## 첨부 파일
