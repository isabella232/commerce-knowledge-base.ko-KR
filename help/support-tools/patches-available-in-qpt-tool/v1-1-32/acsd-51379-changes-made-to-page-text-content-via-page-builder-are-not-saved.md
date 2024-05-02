---
title: "ACSD-51379: 를 통한 페이지의 텍스트 콘텐츠 변경 [!DNL Page Builder] 저장되지 않음"
description: ACSD-51379 패치를 적용하여 를 통해 페이지의 텍스트 콘텐츠에 수행된 변경 사항이 발생하는 Adobe Commerce 문제를 해결합니다. [!DNL Page Builder] 저장되지 않았습니다.
exl-id: e274ca03-b675-4ded-9820-1d60978685d0
feature: Page Builder, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-51379: 를 통한 페이지의 텍스트 콘텐츠 변경 [!DNL Page Builder] 저장되지 않음

ACSD-51379 패치는 를 통해 페이지의 텍스트 콘텐츠에 대한 변경 사항을 적용하는 문제를 해결합니다. [!DNL Page Builder] 저장되지 않았습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32가 설치되어 있습니다. 패치 ID는 ACSD-51379입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

를 통해 페이지의 텍스트 콘텐츠에 적용되는 변경 사항 [!DNL Page Builder] 저장되지 않았습니다.

<u>재현 단계</u>:

1. 관리자에 로그인합니다.
1. 다음으로 이동 **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. 다음 위치에 하나의 행과 하나의 텍스트 요소가 있는 테스트 페이지 만들기: **[!UICONTROL Content]** 탭.
1. 페이지를 저장하고 로 돌아갑니다. **[!UICONTROL Content]** 탭.
1. 텍스트를 선택하고 변경하여 편집합니다.

   **참고:** 편집기를 활성화하지 않고 텍스트를 선택하고 변경하는 경우에만 문제가 재현될 수 있습니다.

1. 다음을 클릭합니다. **[!UICONTROL Save and Close]** 단추를 클릭합니다.
1. 테스트 페이지를 다시 열고 **[!UICONTROL Content]** 탭.

<u>예상 결과</u>:

원본 및 복제된 텍스트 요소에 대해 새 텍스트가 성공적으로 저장됩니다.

<u>실제 결과</u>:

텍스트 요소는 성공적으로 복제되었지만 새 텍스트는 저장되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
