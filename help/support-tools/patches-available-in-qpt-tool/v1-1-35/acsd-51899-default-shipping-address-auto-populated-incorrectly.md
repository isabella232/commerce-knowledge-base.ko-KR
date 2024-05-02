---
title: 'ACSD-51899: 기본 배송 주소가 잘못 입력됨'
description: ACSD-51899 패치를 적용하여 기본 배송 주소가 잘못된 주소로 자동 채워지는 Adobe Commerce 문제를 해결합니다.
feature: Checkout
role: Admin
exl-id: 67100fcd-e98f-4740-8f1f-fcc820f4c75d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-51899: 기본 배송 주소가 잘못 입력됨

ACSD-51899 패치는 기본 배송 주소가 잘못된 주소로 자동 채워지는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있습니다. 패치 ID는 ACSD-51899입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

기본 배송 주소가 잘못된 주소로 자동 채워집니다.

<u>재현 단계</u>:

1. 사용 **매장 픽업** 운송 방법.
1. 만들기 *stock* 및 *소스*.
1. 제품을 만들고 제품을 소스에 할당합니다.
1. 장바구니에 제품을 추가합니다.
1. 클릭 **체크아웃 진행** 미니 장바구니에서.
1. 테스트 이메일 주소를 입력하고 선택 **스토어에서 선택**.
1. 다음을 클릭합니다. **저장소 선택** 단추를 클릭하고 선택할 저장소 위치를 선택합니다.
1. 을(를) 클릭합니다 **다음** 단추를 클릭합니다.
1. 다음 위치로 이동 **홈 페이지** 스토어 로고를 클릭함으로써.
1. 열기 **미니 카트**.
1. 이름이 인 맨 아래 하이퍼링크를 클릭합니다. **장바구니 보기 및 편집**.
1. 클릭 **체크아웃 진행**.
1. 배송 페이지에서 배송 버튼을 클릭합니다.

<u>예상 결과</u>

배송 주소 필드는 을 제외하고 비어 있습니다. *국가, 지역 및 우편 번호*.

<u>실제 결과</u>

기본 배송 주소는 다음으로 자동 채워집니다. *매장 픽업* 페이지를 새로 고친 후 주소를 지정합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
