---
title: "ACSD-51846: 다음과 같은 내부 오류 [!DNL REST API] 페이로드 수준이 확인되지 않음"
description: ACSD-51846 패치를 적용하여 "내부 오류"가 모든 수준으로 발생하는 Adobe Commerce 문제를 해결합니다. [!DNL REST API] 페이로드의 유효성을 검사하지 못했습니다.
feature: REST
role: Developer
exl-id: 17ce5cca-063d-439c-9390-f5e2bf5b696b
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-51846: 내부 오류 [!DNL REST API] 페이로드 수준이 확인되지 않음

ACSD-51846 패치는 모든 수준의 &quot;내부 오류&quot;가 발생하는 문제를 해결합니다. [!DNL REST API] 페이로드의 유효성을 검사하지 못했습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.36이 설치되었습니다. 패치 ID는 ACSD-51846입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3-p2 - 2.4.5-p4

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

의 모든 수준으로 &quot;내부 오류&quot;가 발생합니다. [!DNL REST API] 페이로드의 유효성을 검사하지 못했습니다.

<u>재현 단계</u>:

1. 고객의 장바구니에 제품을 추가합니다.
1. 보내기 [!DNL REST API] 요청 대상 `rest/V1/carts/mine/estimate-shipping-methods` 잘못된 속성 사용 &quot;_거리._&#x200B;끝에 점이 있는 &quot;.

```
 {
    "address": {
         "street.": [
             "\uc11c\uc6b8 \uac15\ubd81\uad6c \ud55c\ucc9c\ub85c166\uae38 2 (-\uc11c\uc6b8 \uac15\ubd81\uad6c \uc218\uc720\ub3d9 269-36)"
         ],
         "city": "pune",
         "region": null,
         "country_id": "IN",
         "postcode": "411015",
         "customer_id": "2",
         "firstname": "test",
         "lastname": "test",
         "middlename": null,
         "prefix": null,
         "suffix": null,
         "vat_id": null,
         "company": null,
         "telephone": "00000000000",
         "fax": null,
         "custom_attributes": []
     }
 }
```

<u>예상 결과</u>:

끝점은 매개 변수의 유효성을 검사하고 `400 status code` 특정 오류 메시지가 표시됩니다. 예:

```
report.CRITICAL: LogicException: Property "Street." does not have accessor method "getStreet." in class "Magento\Quote\Api\Data\AddressInterface". in vendor/magento/framework/Reflection/NameFinder.php:103
```

<u>실제 결과</u>:

끝점이 잘못된 매개 변수의 유효성을 검사하지 않고 `500 status code` 오류.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
