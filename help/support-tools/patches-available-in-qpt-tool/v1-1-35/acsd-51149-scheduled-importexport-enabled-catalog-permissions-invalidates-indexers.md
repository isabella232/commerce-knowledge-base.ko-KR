---
title: '''ACSD-51149: 예약됨 [!UICONTROL ImportExport] 활성화됨 [!UICONTROL Catalog Permissions] 인덱서 무효화'
description: ACSD-51149 패치를 적용하여 예약된 Adobe Commerce 성능 문제를 해결합니다 [!UICONTROL ImportExport] 활성화됨 [!UICONTROL Catalog Permissions] 인덱서를 무효화합니다.
feature: Cache, Data Import/Export
role: Admin
exl-id: 3a26f4be-8e52-407d-bb25-2841458f3aa5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51149: 예약됨 [!UICONTROL ImportExport] 활성화됨 [!UICONTROL Catalog Permissions] 인덱서 무효화

ACSD-51149 패치는 예약된 경우 발생하는 문제를 수정합니다 [!UICONTROL ImportExport] 활성화됨 [!UICONTROL Catalog Permissions] 인덱서를 무효화합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있습니다. 패치 ID는 ACSD-51149입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

예약됨 [!UICONTROL ImportExport] 활성화됨 [!UICONTROL Catalog Permissions] 인덱서를 무효화합니다.

<u>재현 단계</u>:

1. 사용 *[!UICONTROL Catalog Permissions]*.
1. 모든 인덱서를 다음으로 설정 *[!UICONTROL Update by Schedule]*.
1. 간단한 제품을 만듭니다.
1. 다음을 통해 이 제품 내보내기 **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. 내보낸 CSV를 다운로드하고 입력합니다. `<AC root folder>/var/import`.
1. 다운로드한 CSV로 예약된 제품 가져오기를 만듭니다.
1. 전체 색인 재지정을 실행합니다.
1. 인덱서의 상태를 확인합니다. 모든 인덱서가 있어야 합니다. *[!UICONTROL Ready]* 상태.
1. 그리드에서 생성된 예약된 가져오기를 실행합니다.
1. 인덱서의 상태를 다시 확인하십시오.

<u>예상 결과</u>:

모든 인덱서는 *[!UICONTROL Ready]* 상태.

<u>실제 결과</u>:

일부 인덱서가 포함되어 있습니다. *[!UICONTROL Reindex Required]* 상태.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
