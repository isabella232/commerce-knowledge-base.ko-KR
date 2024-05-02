---
title: 'ACSD-48058: 번들 제품에 웹 사이트가 지정되지 않은 경우 제품 가격 리인덱스가 작동하지 않음'
description: ACSD-48058 패치를 적용하여 번들 제품이 웹 사이트에 할당되지 않은 경우 제품 가격 재지수가 작동하지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 691371f1-7f10-4be6-80e4-821e7cf664a6
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-48058: 번들 제품이 웹 사이트를 할당하지 않은 경우 제품 가격 리인덱스가 작동하지 않음

ACSD-48058 패치는 번들 제품이 웹 사이트에 할당되지 않은 경우 제품 가격 재지수가 작동하지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25가 설치되어 있습니다. 패치 ID는 ACSD-48058입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

번들 제품이 웹 사이트에 할당되지 않은 경우 제품 가격 재지수가 작동하지 않습니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자로 이동 > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** 새 번들 제품을 만들거나 기존 번들 제품을 편집합니다.
   * 을(를) 클릭합니다 **[!UICONTROL Product in Websites]** 모든 확인란(웹 사이트)을 탭하거나 선택 취소합니다
   * 제품 저장
1. 색인 재지정을 수행합니다.

<u>예상 결과</u>:

색인 재지정이 성공적으로 수행되었습니다.

<u>실제 결과</u>:

제품 가격 지수를 실행하는 동안 다음 오류가 발생합니다.

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
