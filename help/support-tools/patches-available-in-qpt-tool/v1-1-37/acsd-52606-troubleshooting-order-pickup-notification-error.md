---
title: 'ACSD-52606: 사용자가 "주문 알림 픽업 준비됨"을 클릭할 때 표시되는 오류 메시지'
description: ACSD-52606 패치를 적용하여 사용자가 아이콘을 클릭할 때 오류 메시지가 표시되는 Adobe Commerce 문제를 **[!UICONTROL Notify Order is Ready for Pickup]**.
feature: Orders, User Account
role: Admin, Developer
exl-id: c3e69eb1-90bf-46cf-9b53-110e40e0c3c1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52606: 사용자가 &quot;주문 알림 픽업 준비됨&quot;을 클릭할 때 표시되는 오류 메시지

ACSD-52606 패치는 오류 메시지가 표시되는 문제를 해결합니다 *주문하신 물건이 픽업 준비가 되지 않았습니다* 을 클릭하면 표시됩니다 **[!UICONTROL Notify Order is Ready for Pickup]**. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.37이 설치되었습니다. 패치 ID는 ACSD-52606입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

오류 메시지 *주문하신 물건이 픽업 준비가 되지 않았습니다* 을 클릭하면 화면에 표시됩니다 **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>전제 조건</u>:

인벤토리 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. 새 인스턴스를 설치합니다.
1. 새 소스 및 스톡을 만듭니다.
1. 기본 웹 사이트에 새 소스를 할당합니다.
1. 새로 생성된 소스에 대한 픽업 위치를 활성화합니다.
1. 다음으로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** 및 활성화 **[!UICONTROL In-Store Delivery]**.
1. 만들기 *재고 있음* 를 사용한 간단한 제품 *수량=0* 모든 재고 및 *[!UICONTROL Manage Stock = No]* 두 소스에 모두 할당합니다.
1. 이전 단계에서 만든 제품을 사용하여 프론트엔드에서 주문을 만들고 다음을 선택합니다. *[!UICONTROL In-Store Pickup]* 를 게재 방법으로 사용하십시오.
1. 관리에서 **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. 클릭 **[!UICONTROL Notify order is ready for pickup]**.

<u>예상 결과</u>:

오류 없이 알림을 받습니다.

<u>실제 결과</u>:

다음과 같은 오류 메시지가 표시됩니다. *주문하신 물건이 픽업 준비가 되지 않았습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
