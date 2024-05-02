---
title: 'ACSD-49877: 모바일에서 비디오 자동 재생이 작동하지 않음 [!DNL Safari]'
description: ACSD-49877 패치를 적용하여 모바일에서 비디오 자동 재생 옵션이 작동하지 않는 Adobe Commerce 문제를 해결합니다 [!DNL Safari] 비디오가 원격 비디오 파일에 직접 연결되는 경우입니다.
exl-id: 454f7cec-29b9-485b-93be-2a4f2eb77da7
feature: CMS
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877: 모바일에서 비디오 자동 재생이 작동하지 않음 [!DNL Safari]

ACSD-49877은 모바일에서 자동 재생 옵션이 표시되는 문제를 해결합니다 [!DNL Safari] 비디오가 원격 비디오 파일에 직접 연결된 경우 작동하지 않습니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되었습니다. 패치 ID는 ACSD-49877입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 [!magento/quality 패치] 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색]. 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

모바일에서는 비디오 자동 재생이 작동하지 않습니다. [!DNL Safari] 비디오가 스트리밍 서비스가 아닌 원격 비디오 파일에 직접 연결된 경우.

<u>전제 조건</u>:
[!DNL Page Builder] 모듈이 설치되었습니다.

<u>재현 단계</u>:

1. 새 CMS 페이지를 만들고 **[!UICONTROL Content Value]** 포함 [!DNL Page Builder].
1. 추가 *탭* 요소를 콘텐츠에 추가하고 *비디오 요소* 의 내부 *탭*.
1. 이제 톱니바퀴 버튼을 클릭하여 *비디오 요소*.
1. mp4 비디오 파일에 대한 링크를 [!UICONTROL Video URL] 필드.
1. 다음을 표시합니다. **[!UICONTROL Autoplay]** 다음으로 필드 *예*.
1. 클릭 **[!UICONTROL Save]**.
1. 다음에서 최근에 만든 페이지를 엽니다. [!DNL Safari] iPhone 사용.

<u>예상 결과</u>

자동 재생 옵션은에서 작동합니다. [!DNL Safari] iPhone 사용.

<u>실제 결과</u>

자동 재생 옵션이 작동하지 않음 [!DNL Safari] iPhone 사용.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
