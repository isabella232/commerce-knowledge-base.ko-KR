---
title: "MDVA-42645: 관리자가 비활성화된 스토어 크레딧에 대한 보상 포인트를 환불할 수 없음"
description: MDVA-42645 패치는 저장소 신용 기능이 비활성화된 경우 관리자가 보상 포인트를 환불할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42645입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 8e8f8c07-c1a2-4031-a2fb-cb737165dc2c
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-42645: 관리자가 비활성화된 스토어 크레딧에 대한 보상 포인트를 환불할 수 없음

MDVA-42645 패치는 저장소 신용 기능이 비활성화된 경우 관리자가 보상 포인트를 환불할 수 없는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치되어 있습니다. 패치 ID는 MDVA-42645입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자는 스토어 신용 기능이 비활성화된 경우 보상 포인트를 환불할 수 없습니다.

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. 새 고객 계정을 만들고 몇 가지 보상 포인트를 추가합니다.
1. 다음 위치로 이동하여 스토어 신용 기능 비활성화 **저장** > 설정 > **구성** > **고객** > **고객 구성** > **저장소 크레딧 옵션**.
1. 보상 포인트가 지정된 고객으로 로그인합니다.
1. 장바구니에 제품을 추가하고 체크아웃으로 이동합니다.
1. 결제 섹션에서 보상 포인트를 사용한 후 주문합니다.
1. 관리자에서 주문을 열고 주문의 송장을 발행합니다.
1. 을(를) 클릭합니다 **대변 메모** 신규 대변 메모를 생성하기 위한 링크입니다.
1. 하단의 환불 보상 포인트 옵션을 선택하고 **오프라인 환불**.

<u>예상 결과</u>:

* 대변 메모가 정상적으로 생성되었습니다.
* 보상 포인트가 성공적으로 환급되었습니다.

<u>실제 결과</u>:

다음과 같은 오류 메시지가 표시됩니다. *주문금액보다 더 많은 점포 크레딧을 사용할 수 없습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
