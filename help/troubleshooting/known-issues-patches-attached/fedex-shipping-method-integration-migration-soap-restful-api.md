---
title: '[!DNL FedEx] SOAP에서 RESTful API로 배송 방법 통합 마이그레이션'
promoted: true
description: 다음을 처리하기 위해 패치 적용 [!DNL FedEx] Adobe Commerce 2.4.4-p4 - 2.4.6-pX용 SOAP에서 RESTful API로 배송 방법 통합 마이그레이션.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# [!DNL FedEx] SOAP에서 RESTful API로 배송 방법 통합 마이그레이션

이 문서에서는 의 문제를 해결하는 패치를 제공합니다. [!DNL FedEx] Adobe Commerce 2.4.4-p4 - 2.4.6-pX용 SOAP에서 RESTful API로 배송 방법 통합 마이그레이션.

[!DNL FedEx Web Services] 추적, 주소 유효성 검사 및 우편 번호 확인 WSDLS(Web Services Definition Language)는 2024년 5월 15일에 사용이 중단됩니다. SOAP 기반 [!DNL FedEx Web Services] 이(가) 개발 억제 상태에 있으며 로 대체되었습니다. [!DNL FedEx] RESTFUL API. 자세한 내용은 다음을 참조하십시오. [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

이 변경 사항은 현재 항목에 영향을 줍니다. [!DNL FedEx] Adobe Commerce의 배송 방법 통합 구현이며, 현재 구현을 수정하고 더 이상 사용되지 않는 SOAP API에서 최신 API로 마이그레이션해야 합니다. [!DNL FedEx] RESTFUL API.

2024년 5월 15일부터 Adobe Commerce 고객은 현재 버전을 사용할 수 없습니다 [!DNL FedEx] 배송 방법 통합에 따라 Adobe은 Adobe Commerce 2.4.4 이상 고객이 최신 버전을 사용할 수 있도록 하는 이 핫픽스를 출시하고 있습니다 [!DNL FedEx] 더 이상 사용되지 않는 SOAP 대신 RESTFUL API입니다.


## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure 및 on-premise 및 Magento Open Source:

* 2.4.4-p4
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6-pX

## 원인

다음 [!DNL FedEx] 해당 SOAP 기반 API를 더 이상 사용하지 않으며 대신 RESTful API로 대체되었습니다. 을(를) 참조하십시오 [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

## 솔루션

Adobe Commerce/Magento Open Source 버전에 따라 다음과 같이 첨부된 패치를 사용하십시오.

2.4.4+, 2.4.5+ 및 2.4.6+ 버전에서 문제를 해결하려면 아래 Adobe Commerce/Magento Open Source 버전에 해당 패치를 적용해야 합니다.

## 패치

Adobe Commerce/Magento Open Source 버전에 따라 다음과 같이 첨부된 패치를 사용하십시오.

### 버전 2.4.4-p4의 경우:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### 2.4.5, 2.4.5-pX 버전의 경우:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### 2.4.6, 2.4.6-pX 버전의 경우:


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


## 패치 적용 방법

파일의 압축을 풀고 다음을 확인합니다. [Adobe에서 제공하는 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) 지침에 대해서는 지원 기술 자료에서 참조하십시오.

## 패치가 적용되었는지 확인하는 방법

문제가 패치되었는지 쉽게 확인할 수 없는 점을 고려하면 패치가 정상적으로 적용되었는지 확인할 수 있습니다. 다음을 사용합니다(예: *AC-*)를 확인할 패치입니다.

<u>다음 단계를 수행하여 이 작업을 수행할 수 있습니다</u>:

1. [설치 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. 다음 명령을 실행합니다.

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. 다음과 유사한 출력이 표시되어야 합니다. 여기서 AC-9363은 *적용됨* 상태:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
