---
title: 'ACSD-49480: 작동하지 않는 후속 규칙 버리기'
description: ACSD-49480 패치를 적용하여 다음과 같은 Adobe Commerce 문제를 해결합니다. [!UICONTROL Cart Price Rule - Discard Subsequent Rules] 은(는) 의도한 대로 작동하지 않습니다.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] 은(는) 의도한 대로 작동하지 않습니다.

ACSD-49480 패치를 사용하면 다음과 같은 문제가 해결됩니다. [!UICONTROL Cart Price Rule - Discard Subsequent Rules] 은(는) 의도한 대로 작동하지 않습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.32가 설치되어 있습니다. 패치 ID는 ACSD-49480입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] 은(는) 의도한 대로 작동하지 않습니다.

<u>재현 단계</u>:

1. 만들기 **[!UICONTROL Cart Price Rule]** 쿠폰 코드 (이름 지정 *테스트*)에 $10 할인을 제공하는 *제품 ID 1* 다음에서 **[!UICONTROL Actions]** 탭 [!UICONTROL Discard Subsequent Rules] 을 로 설정 *[!UICONTROL Yes]* 및 [!UICONTROL Priority] 을 로 설정 *1*.
1. 다른 항목 만들기 **[!UICONTROL Cart Price Rule]** (으)로 $5 할인을 제공하는 쿠폰 코드 없음 *제품 ID 2* 다음에서 **[!UICONTROL Actions]** 탭 [!UICONTROL Priority] 을 로 설정 *2*. 여기에서는 다음을 위한 글로벌 세일이라고 가정합니다. *제품 ID 2*.
1. 프론트엔드 사이트로 이동하여 추가 *제품 ID 1* 및 *제품 ID 2* 장바구니에 넣으십시오.
1. 적용 *테스트* 쿠폰 코드.

<u>예상 결과</u>

* *할인 1* 다음에 적용됨 *제품 ID 1*.
* *할인 2* 다음에 적용됨 *제품 ID 2*.

<u>실제 결과</u>

* 전용 *할인 1* 다음에 적용됨 *제품 ID 1*.
* *할인 2* 이(가)에 적용되지 않음 *제품 ID 2*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
