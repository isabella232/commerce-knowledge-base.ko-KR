---
title: 'ACSD-47336: [!UICONTROL Something went wrong] Adobe Commerce 관리자에서 알림을 해제할 때 오류 발생'
description: ACSD-47336 패치를 적용하여 사용자에게 표시되는 Adobe Commerce 문제를 해결합니다 [!UICONTROL Something went wrong] 에서 알림을 닫을 때 오류 발생 [!DNL Commerce] 관리자.
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336: _[!UICONTROL Something went wrong]_Adobe Commerce 관리자에서 알림을 해제할 때 오류 발생

ACSD-47336 패치는 사용자에게 표시되는 문제를 해결합니다. _[!UICONTROL Something went wrong]_에서 알림을 닫을 때 오류 발생 [!DNL Commerce] 관리자. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되었습니다. 패치 ID는 ACSD-47336입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법): 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자에게 표시됨 _[!UICONTROL Something went wrong]_에서 알림을 닫을 때 오류 발생 [!DNL Commerce] 관리자.

<u>재현 단계</u>:

1. 대량 작업을 수행합니다(예: 제품 그리드에서 제품 속성의 대량 업데이트).
1. 작업을 완료합니다(예: 실행). `bin/magento queue:consumer:start product_action_attribute.update`).
1. 새로 고침 [!DNL Commerce] 관리 페이지에서 관리 알림 섹션을 확장하고 **[!UICONTROL Dismiss All Completed Tasks]** 링크를 클릭합니다.

<u>예상 결과</u>:

다음 _[!UICONTROL Something went wrong]_완료된 작업을 지울 때 오류가 표시되지 않아야 합니다.

<u>실제 결과</u>:

다음 _[!UICONTROL Something went wrong]_오류가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
