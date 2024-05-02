---
title: Adobe Commerce 상태 열에 내보낸 제품 CSV 파일이 없음
description: 이 문서에서는 내보낸 제품이 포함된 CSV 파일에서 상태 열을 찾을 수 없는 문제에 대한 해결 방법을 제공합니다.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce 상태 열에 내보낸 제품 CSV 파일이 없음

이 문서에서는 내보낸 제품이 포함된 CSV 파일에서 상태 열(예: 제품의 활성화 또는 비활성화 여부 표시)을 찾을 수 없는 경우의 문제에 대한 해결 방법을 제공합니다. 제품의 상태는 로 표시됩니다. [!UICONTROL product_online] 열.

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 메서드) 모두 [지원되는 버전](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 문제

다음 항목을 찾을 수 없습니다. [!UICONTROL status] 내보낸 제품이 포함된 CSV 파일의 열입니다. 따라서, 예를 들어 모든 SKU의 CSV를 상태와 함께 내보내지만 테이블에 [!UICONTROL status] 열.

<u>재현 단계:</u>

1. Adobe Commerce 관리에서 다음을 선택합니다. **[!UICONTROL System]**, 아래 **[!UICONTROL Data Transfer]** 선택 **[!UICONTROL Export]**.
1. 다음에서 **[!UICONTROL Export Settings]** 섹션에서 다음을 선택합니다. **[!UICONTROL Entity Type]** 드롭다운 **[!UICONTROL Products]**.
1. 검색 대상 **[!UICONTROL status]**, 아래에 나열됨 **[!UICONTROL Attribute Code]**. 사용 가능한 속성 목록에 해당 속성 코드가 표시됩니다(**[!UICONTROL Enable Product]**).
1. 클릭 **[!UICONTROL Export]**.

<u>예상 결과:</u>

방금 내보낸 CSV 파일에 라는 레이블이 지정된 열이 있습니다 [!UICONTROL status].

<u>실제 결과:</u>

레이블이 지정된 열이 표시되지 않습니다. [!UICONTROL status] 을 추가합니다.

## 원인

제품의 상태 특성 이름이 CSV 파일에서 변경되었습니다. 이제 다음과 같습니다. [!UICONTROL product_online] 열.

## 솔루션

1. 선택 **[!UICONTROL System]**, 아래 **[!UICONTROL Data Transfer]** 선택 **[!UICONTROL Import]**.
1. 클릭 **[!UICONTROL Download Sample File]**.
1. 다음을 볼 수 있습니다. [!UICONTROL product_online] csv 파일의 열입니다.

## 관련 읽기

* [CSV 파일 작업](https://docs.magento.com/user-guide/system/data-csv.html) 사용 안내서에서 참조하십시오.
* [제품 내보내기 속성 참조](https://docs.magento.com/user-guide/system/data-attributes-product.html) 사용 안내서에서 참조하십시오.
