---
title: 'ACSD-51890: [!UICONTROL Submit review] 단추를 여러 번 클릭할 수 있음'
description: ACSD-51890 패치를 적용하여 다음과 같은 Adobe Commerce 문제를 해결합니다. [!UICONTROL Submit Review] 없이 단추를 여러 번 클릭할 수 있습니다. [!DNL Google reCAPTCHA v3] 유효성 검사.
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890: **[!UICONTROL Submit Review]** 없이 단추를 여러 번 클릭할 수 있습니다. **[!DNL Google reCAPTCHA v3]** 유효성 검사

>[!NOTE]
>
>이 패치는 다음으로 대체됩니다. [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

ACSD-51890 패치를 사용하면 다음과 같은 문제가 해결됩니다. **[!UICONTROL Submit Review]** 없이 단추를 여러 번 클릭할 수 있습니다. **[!DNL Google reCAPTCHA v3]** 유효성 검사. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35가 설치되어 있습니다. 패치 ID는 ACSD-51890입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음 **[!UICONTROL Submit Review]** 단추를 여러 번 클릭할 수 있지만 **[!DNL Google reCAPTCHA v3]** 유효성 검사.

<u>재현 단계</u>:

1. 사용 **[!DNL Google reCAPTCHA v3]** 제품 리뷰용.
1. 제품 페이지를 열고 로 이동합니다. **[!UICONTROL Review]** 섹션 및 다음을 확인합니다. [!DNL reCAPTCHA] 가 표시됩니다.
1. 검토 양식을 작성하고 **[!UICONTROL Submit Review]** 가능한 한 빨리 여러 번 버튼을 누릅니다.
1. 를 엽니다. **[!UICONTROL Review]** 섹션에 있는 마지막 항목이 될 필요가 없습니다.

<u>예상 결과</u>

중복 검토는 생성되지 않습니다.

<u>실제 결과</u>

중복 검토가 만들어집니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 다음에서 [!DNL Quality Patches Tool] 가이드.
