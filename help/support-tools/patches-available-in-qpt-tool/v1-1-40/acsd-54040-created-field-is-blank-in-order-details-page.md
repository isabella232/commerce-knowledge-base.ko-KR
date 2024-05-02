---
title: 'ACSD-54040: [!UICONTROL Created] B2B 모듈이 활성화된 경우 필드는 주문 세부 사항에 대해 비어 있습니다.'
description: ACSD-54040 패치를 적용하여 다음과 같은 Adobe Commerce 문제를 해결합니다. [!UICONTROL Created] B2B 모듈이 활성화되면 주문 세부 사항 페이지의 필드가 비어 있습니다.
feature: B2B
role: Admin, Developer
exl-id: 5c420b94-43e1-40ac-9482-8a2d42f173d9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-54040: *[!UICONTROL Created]* B2B 모듈이 활성화되면 필드가 비어 있는 주문 세부 사항.

ACSD-54040 패치를 사용하면 다음과 같은 문제가 해결됩니다. *[!UICONTROL Created]* B2B 모듈이 활성화되면 주문 세부 사항 페이지의 필드는 비어 있습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40이 설치되었습니다. 패치 ID는 ACSD-54040입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p5, 2.4.4-p6, 2.4.5-p4, 2.4.5-p5

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

B2B 모듈이 활성화되면 *[!UICONTROL Created]* [주문 세부 사항] 페이지의 필드는 비어 있습니다.

<u>재현 단계</u>:

1. B2B 모듈로 Adobe Commerce을 설치합니다.
1. 새 고객을 만들고 주문합니다.
1. 프론트엔드에 있는 주문 세부 정보로 이동하여 *[!UICONTROL Created]* 필드.

<u>예상 결과</u>:

다음 *[!UICONTROL Created]* 필드에는 주문이 만들어진 날짜가 표시됩니다.

<u>실제 결과</u>:

다음 *[!UICONTROL Created]* 필드가 비어 있음

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
