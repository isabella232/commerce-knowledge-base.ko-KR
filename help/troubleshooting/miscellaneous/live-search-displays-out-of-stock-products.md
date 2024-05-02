---
title: '''[!DNL Live Search] 관리자''의 재고 상태 설정에 관계없이 품절 제품을 표시합니다.'
description: 이 문서에서는 검색 팝오버가 일부 항목을 반환하는 동안 PLP(제품 목록 페이지)에 *선택* 오류와 일치하는 제품을 찾을 수 없습니다.*가 표시되는 알려진 문제에 대해 설명합니다.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] 관리자의 재고 상태 설정에 관계없이 품절 제품을 표시합니다.

>[!IMPORTANT]
>
>이 문제는에서 수정되었습니다. [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html). 최신 버전을 설치하려면 다음을 참조하십시오 [업데이트 중 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) 사용 안내서에서 다음을 수행합니다.

이 문서에서는 PLP(제품 목록 페이지)에 표시되는 알려진 문제에 대한 정보를 제공합니다 *선택 항목과 일치하는 제품을 찾을 수 없습니다.* 검색 팝오버가 일부 항목을 반환하는 동안 오류가 발생했습니다.

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 메서드) 2.4.x

## 문제

[!DNL Live Search] Adobe Commerce 관리자의 재고 상태 설정에 관계없이 검색 결과를 표시합니다. 다음의 경우에도 **[!UICONTROL Display Out-of-Stock Products]** 이(가) (으)로 설정됨 *아니요*&#x200B;로 나열된 상태로 남아 있는 문제가 해결되었습니다. PLP 오류가 발생합니다. *선택 항목과 일치하는 제품을 찾을 수 없습니다.*.

<u>재현 단계</u>:

1. 카테고리를 만들고 제품을 추가합니다. (예: 범주 = _청바지_, 제품1 = _Blue Jeans_, 제품2 = _Black Jeans_)
1. 해당 범주의 모든 제품을 품절합니다.
1. 설정 **[!UICONTROL Display Out-of-Stock Products]** 끝 *아니요*.
1. 상점 앞에서 들어갑니다 *청바지* 을 클릭합니다.
1. 클릭 **[!UICONTROL View All]** 팝업에서.

<u>예상 결과</u>:

다음을 볼 수 있습니다. *선택 항목과 일치하는 제품을 찾을 수 없습니다.* PLP에 메시지가 표시되고 검색 팝업에는 제품이 표시되지 않습니다.

<u>실제 결과</u>:

다음을 볼 수 있습니다. *선택 항목과 일치하는 제품을 찾을 수 없습니다.* PLP에 메시지가 표시되고 두 제품 모두 검색 팝업에 표시됩니다.

## 솔루션

현재 이 문제에 대한 해결 방법은 없습니다. 당사 [!DNL Live Search] 팀은 곧 을 구성할 설정을 제공합니다. [!DNL Live Search] 을 클릭하여 제품을 올바르게 표시합니다.

## 관련 읽기

[설치 [!DNL Live Search]](https://docs.magento.com/user-guide/live-search/install.html) 사용 안내서에서 참조하십시오.
