---
title: 'ACSD-51528: snake_case 서식에 대한 다양한 동작'
description: ACSD-51528 패치를 적용하여 snake_case 서식에 다른 동작이 있는 Adobe Commerce 문제를 수정합니다.
exl-id: dd878321-8032-41f3-8dcd-acb0cc023b44
feature: Variables
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-51528: snake_case 서식에 대한 다양한 비헤이비어

ACSD-51528 패치는 snake_case 서식에 대한 다양한 동작을 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.32가 설치되어 있습니다. 패치 ID는 ACSD-51528입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

snake_case 서식에 대한 다양한 비헤이비어

<u>재현 단계</u>:

1. 테스트 `\Magento\Framework\Api\DataObjectHelper::populateWithArray` 함수 내에 여러 가지 속성 이름이 있습니다.
1. 다음과 같은 이름의 속성 *NewPName* 으로 변환되어야 합니다. *new_p_name*, 대신 로 변환됩니다. *new_name*.
1. 또한 을 사용할 때도 *getNewPName* 개체에서 함수, *null* 다음 이유로 반환됩니다. *추상 모델* 이(가) 호출을 (으)로 올바르게 변환합니다. *new_p_name* 두 기능을 서로 호환되지 않도록 하는 것입니다.

<u>예상 결과</u>

다음 **[!UICONTROL populateWithArray]** 함수는 오브젝트 속성을 snake_case로 올바르게 변환하여 **[!DNL AbstractModel's]** `Getters` 및 `Setters`.

<u>실제 결과</u>

사용 시 **[!UICONTROL populateWithArray]** 함수, 이름에 두 개 이상의 대문자가 연속으로 포함된 개체 속성은 최종 데이터 배열에서 snake_case 변환이 잘못되도록 합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
