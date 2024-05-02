---
title: '''ACSD-46519: [!UICONTROL product_count] 위치: [!UICONTROL categoryList] [!DNL GraphQL] 쿼리가 앵커 범주에 대해 0을 반환합니다.'
description: ACSD-46519 패치를 적용하여 을 사용할 때 발생하는 Adobe Commerce 문제를 해결합니다. [!UICONTROL categoryList] [!DNL GraphQL] 하위 카테고리를 가져오는 메서드 [!UICONTROL product_count] 상위 카테고리에 대해 0으로 표시합니다.
exl-id: b71be3e6-6235-4e96-848b-d61eda973d98
feature: Categories, GraphQL, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-46519: [!UICONTROL product_count] 위치: [!UICONTROL categoryList] [!DNL GraphQL] 쿼리가 앵커 범주에 대해 0을 반환합니다.

ACSD-46519 패치는 다음과 같은 문제를 해결합니다. [!UICONTROL product_count] 위치: [!UICONTROL categoryList] [!DNL GraphQL] 쿼리는 앵커 범주에 대해 0을 반환합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23이 설치되었습니다. 패치 ID는 ACSD-46519입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**
* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.5-p1

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음의 경우 [!UICONTROL categoryList] [!DNL GraphQL] 메서드는 가 표시하는 하위 범주를 가져오는 데 사용됩니다. [!UICONTROL product_count] 상위 카테고리에 대해 0으로 표시합니다.

<u>재현 단계</u>:

1. 다음 사용 [!DNL GraphQL] 을(를) 사용하여 범주 계층 구조를 가져오도록 요청 [!UICONTROL product_count]:

<pre><code>
{
  categoryList(filters: { ids: { eq: "2" } }) {
    id
    name
    product_count
    level
    children {
      name
      product_count
      level
      children {
        name
        product_count
        level
        children {
          name
          product_count
          level
          children {
            name
            product_count
            level
          }
        }
      }
    }
  }
}
</code></pre>

<u>예상 결과</u>:

상위 카테고리가 고정된 카테고리일 경우 [!UICONTROL product_count] 모든 수준에서 하위 범주 제품 수의 합계를 표시합니다.

<u>실제 결과</u>:

상위 카테고리가 고정된 카테고리인 경우 제품은 카테고리 레벨 2 및 아래쪽에 대해 0으로 표시됩니다.

<pre><code>
{
    "data": {
        "categoryList": [
            {
                "id": 2,
                "name": "Default Category",
                "product_count": 186,
                "level": 1,
                "children": [
                    {
                        "name": "What's New",
                        "product_count": 0,
                        "level": 2,
                        "children": []
                    },
                    {
                        "name": "Women",
                        "product_count": 0,
                        "level": 2,
                        "children": [
                            {
                                "name": "Tops",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            },
                            {
                                "name": "Bottoms",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            }
                        ]
                    },
                    ...
                ]
            }
        ]
    }
}
</code></pre>

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
