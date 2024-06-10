---
title: '[!DNL UPS] 에서 배송 방법 통합 마이그레이션 [!DNL SOAP] 끝 [!DNL RESTful API]'
promoted: true
description: 다음을 처리하기 위해 패치 적용 [!DNL UPS] 에서 배송 방법 통합 마이그레이션 [!DNL SOAP] 끝 [!DNL RESTful API] Adobe Commerce 2.4.4 - 2.4.6-pX용
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL UPS] 에서 배송 방법 통합 마이그레이션 [!DNL SOAP] 끝 [!DNL RESTful API]

>[!NOTE]
>
>이전에 이 문서에서 세 개의 패치 중 하나를 업로드한 경우 **2024년 6월 6일**: 다음 이유로 이 문제가 발생하는 경우: [!DNL Metric System/SI] 측정(킬로그램 및 센티미터)을 사용하지 않는 경우에는 Adobe Commerce/Magento Open Source 2.4.4+/2.4.5+/2.4.6+ 버전에 대해 이 문서에 이제 게시된 새로운 업데이트 패치 중 하나를 다시 적용해야 합니다. 그렇지 않으면 다음을 선택할 수 없습니다. [!DNL Metric System/SI] 측정 **킬로그램** 및 **센티미터** 다음에서 [!DNL UPS] 의 배송 방법 **[!DNL Admin configuration]**. 이러한 새 패치는 이전에 릴리스된 패치와 호환됩니다. 이 문제는 다음에 예정된 Adobe Commerce 버전 2.4.7-p1 릴리스의 범위에서 영구적으로 수정됩니다. **2024년 6월 11일**.

>[!NOTE]
>
>이전에 이 문서에서 세 개의 패치 중 하나를 업로드한 경우 **2023년 10월 10일**, 이제 이 문서에 게시된 이러한 패치 중 하나를 Adobe Commerce/Magento Open Source의 2.4.4+/2.4.5+/2.4.6+ 버전에 대해 다시 적용해야 합니다. 그렇지 않으면 특정 패치를 선택하고 구성할 수 없기 때문입니다 [!DNL UPS] 의 배송 방법 **[!DNL Admin configuration]**, 그리고 모든 기능을 활성화해야 합니다. 이러한 새 패치는 이전에 릴리스된 패치와 호환됩니다.

이 문서에서는 의 문제를 해결하는 패치를 제공합니다. [!DNL United Parcel Service (UPS)] 에서 배송 방법 통합 마이그레이션 [!DNL SOAP] 끝 [!DNL RESTful API] Adobe Commerce 2.4.4 - 2.4.6-pX용

에 대한 최신 업데이트에 따라 [!DNL UPS API] 보안 모델, [!DNL UPS] 이(가) 다음을 구현했습니다. [!DNL OAuth 2.0] 모두를 위한 보안 모델 [!DNL APIs] (자세한 내용은 [[!DNL UPS] 개발자 포털 액세스 키 마이그레이션 안내서](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914))를 사용하여 사기를 줄이고 보안을 강화할 수 있습니다 [!DNL API] 기능.

이 변경 사항은 현재 항목에 영향을 줍니다. [!DNL UPS] Adobe Commerce의 배송 방법 통합 구현과 현재 구현을 수정하고 [!DNL SOAP API] (으)로 [!DNL RESTful API] 다음을 지원할 수 있음 [!DNL OAuth 2.0] 인증 프로토콜입니다.

**2024년 6월에 시작**, Adobe Commerce 판매자는 현재 제품과 거래할 수 없습니다. [!DNL UPS] 통합되었으므로 Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ 판매자가 최신 버전으로 마이그레이션할 수 있는 이 핫픽스가 출시됩니다 [!DNL UPS REST APIs].

이 문제는 Adobe Commerce/Magento Open Source 버전 2.4.7에서 수정되며, 이 수정 사항은 2023년 10월 2.4.7-beta2 릴리스에도 포함될 예정입니다.

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure 및 on-premise 및 Magento Open Source:

* 2.4.4
* 2.4.4-pX
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6-pX

## 원인

다음 [!DNL UPS] 릴리스: [보안 업데이트 [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

유럽 연합 (다른 출처가 동일한 문제를 경험할 수 있음)이 선적 출처와 동일한 경우 다음 항목에 오류가 발생합니다. [!DNL UPS REST] 요청: &quot;*선적 단위는 KGS/IN 또는 LBS/CM 또는 OZS/CM일 수 없습니다.*&quot;

## 솔루션

Adobe Commerce/Magento Open Source 버전에 따라 다음과 같이 첨부된 패치를 사용하십시오.

2.4.4+, 2.4.5+ 및 2.4.6+ 버전에서 문제를 해결하려면 아래 Adobe Commerce/Magento Open Source 버전에 해당 패치를 적용해야 합니다.

## 패치

Adobe Commerce/Magento Open Source 버전에 따라 다음과 같이 첨부된 패치를 사용하십시오.

### 2.4.4, 2.4.4-pX 버전의 경우:

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### 2.4.5, 2.4.5-pX 버전의 경우:

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### 2.4.6, 2.4.6-pX 버전의 경우:

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

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
