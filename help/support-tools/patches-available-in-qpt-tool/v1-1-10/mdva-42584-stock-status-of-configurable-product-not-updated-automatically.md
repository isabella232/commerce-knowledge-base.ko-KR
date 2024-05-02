---
title: 'MDVA-42584: 구성 가능한 제품의 재고 상태가 자동으로 업데이트되지 않음'
description: MDVA-42584 패치는 구성 가능한 제품의 단순 제품이 업데이트될 때 재고 상태가 자동으로 업데이트되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42584입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584: 구성 가능한 제품의 재고 상태가 자동으로 업데이트되지 않음

MDVA-42584 패치는 구성 가능한 제품의 단순 제품이 업데이트될 때 재고 상태가 자동으로 업데이트되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치되었습니다. 패치 ID는 MDVA-42584입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

백엔드에서 구성 가능한 제품의 재고 상태는 간단한 제품이 로 설정된 경우 자동으로 업데이트되지 않습니다. **재고 있음** api 또는 가져오기를 통해.

<u>전제 조건</u>:

MSI가 설치되었습니다.

<u>재현 단계</u>:

1. 구성 가능한 제품 만들기, **InvCheck001**, 두 가지 옵션 포함: **InvCheck001-M** 및 **InvCheck001-L**.
1. 단순 제품 모두 수량이 있어야 하며 다음과 같아야 합니다. **재고 있음** 구성 가능한 제품도 **재고 있음** 백엔드에서.
1. 이제 단순 제품을 모두 업데이트하고 수량을 (으)로 설정합니다. **0** 및 다음으로 재고 상태 **품절**.
1. 구성 가능한 제품을 새로 고치고 재고 상태가 (으)로 업데이트되었는지 확인합니다. **품절**.
1. 다음 API 끝점을 사용하고 간단한 제품을 설정하십시오 **InvCheck001-M** 끝 **재고 있음** 수량이 0보다 큰 경우

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. 백엔드로 이동하여 간단한 제품의 수량과 재고 상태를 확인합니다 **InvCheck001-M**. 다음으로 업데이트되었습니다. **재고 있음**.
1. 구성 가능한 제품을 새로 고치고 재고 상태를 확인합니다.

<u>예상 결과</u>:

구성 가능한 제품의 재고 상태 **InvCheck001** 백엔드에서 가 로 자동 업데이트됩니다. **재고 있음**.

<u>실제 결과</u>:

구성 가능한 제품의 재고 상태는 여전히 입니다 **품절**.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
