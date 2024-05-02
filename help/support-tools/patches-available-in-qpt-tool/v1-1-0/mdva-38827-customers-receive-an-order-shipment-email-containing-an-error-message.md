---
title: 'MDVA-38827: 고객이 이메일을 통해 주문 배송 오류를 수신함'
description: "MDVA-38827 패치는 고객이 다음 오류 메시지가 포함된 주문 배송 이메일을 받는 문제를 해결했습니다. *죄송합니다. 이 콘텐츠를 생성하는 동안 오류가 발생했습니다.* 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38827입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정될 예정입니다."
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827: 고객이 이메일을 통해 주문 배송 오류 수신

MDVA-38827 패치는 고객이 다음 오류 메시지가 포함된 주문 배송 이메일을 받는 문제를 해결합니다. *죄송합니다. 이 콘텐츠를 생성하는 동안 오류가 발생했습니다.*. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0이 설치되었습니다. 패치 ID는 MDVA-38827입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

클라우드 인프라의 Adobe Commerce 2.4.2-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객에게 이메일로 발송 통지 옵션을 선택하면 고객에게 다음 오류 메시지가 포함된 이메일이 발송됩니다. *죄송합니다. 이 콘텐츠를 생성하는 동안 오류가 발생했습니다.*.

<u>재현 단계</u>:

1. 다음으로 이동 **마케팅** > **통신** > **이메일 템플릿** 및 선택 **새 템플릿 추가**.
   * 선택 **Magento 판매** > **새 배송**.
   * 클릭 **템플릿 로드**.
   * 템플릿 이름(예: Core Shipping Template)을 추가하고 **저장**.
1. 다음으로 이동 **저장** > 설정 > **구성** > **판매** > **영업 이메일**:
   * 사용 **배송 댓글**.
   * 선택 **핵심 배송 템플릿** (1단계의 &quot;템플릿 이름 추가&quot; 부분 참조) Guest의 Shipment Comment Email Template 및 Shipment Comment Email Template 아래에 있습니다.
1. 주문하십시오. 관리 패널 로 이동합니다. > **판매** > **주문**, 클릭 **보기**&#x200B;를 클릭한 다음 주문을 배송합니다.
1. 주문 상태가 보류 중에서 처리로 변경됩니다.
1. 클릭 **배송** 왼쪽 사이드바 메뉴에서 **보기** 주문을 확인합니다.
1. 다음에 주석 추가 **댓글 텍스트** 아래 **배송 내역** 확인란을 선택합니다. **고객에게 이메일로 알림**.
1. 클릭 **의견 제출**.

<u>예상 결과</u>:

배송 의견이 포함된 판매 이메일이 생성됩니다.

<u>실제 결과</u>:

이메일에 다음과 같은 오류 메시지가 수신됩니다. *죄송합니다. 이 콘텐츠를 생성하는 도중 오류가 발생했습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
