---
title: "ACSD-54961: 제한된 관리자는 대량 업데이트를 할 수 없습니다. [!UICONTROL Product Review status]"
description: ACSD-54961 패치를 적용하여 제한된 관리자가 제품 검토 상태를 일괄 업데이트할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: 26c5bacd-21de-4533-a7b6-4acbacd38fec
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54961: 제한된 관리자는 대량 업데이트를 할 수 없습니다. [!UICONTROL Product Review status]

ACSD-54961 패치는 제한된 관리자가 대량 업데이트를 할 수 없는 문제를 해결합니다 [!UICONTROL Product Review status]. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40이 설치되었습니다. 패치 ID는 ACSD-54961입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제한된 관리자는 대량 업데이트를 할 수 없습니다. [!UICONTROL Product Review status].

<u>재현 단계</u>:

1. 추가 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. 2번째 스토어에 제품을 추가한 다음 리뷰를 추가합니다.
1. 두 번째 저장소에만 액세스할 수 있는 제한된 관리자 사용자를 만듭니다.
1. 제한된 관리자로 로그인한 다음 로 이동합니다. **[!UICONTROL  Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]**, 및 설정 **상태** 끝 *승인됨* 또는 *보류 중*.

<u>예상 결과</u>:

제한된 관리자는 을 사용하여 검토를 업데이트할 수 있습니다. **[!UICONTROL Mass Update]** 작업.

<u>실제 결과</u>:

을(를) 사용하여 검토를 업데이트하는 도중 오류 발생 **[!UICONTROL Mass Update]** 작업.<br>
다음 `var/log/exception.log` 에는 유사한 오류가 포함되어 있습니다.

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
