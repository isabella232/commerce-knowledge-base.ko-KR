---
title: '''ACSD-56842: ''설정''을 실행한 후 지연된 프록시 및 프록시 팩토리가 누락됨:di:컴파일`'''
description: ACSD-56842 패치를 적용하여 'setup'을 실행한 후 지연된 프록시 및 프록시 팩토리가 누락된 Adobe Commerce 문제를 수정합니다:di:컴파일`.
feature: Deploy, Catalog Management
role: Admin, Developer
exl-id: 2d12e36c-d8b7-4253-91d8-28b50477ccd9
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-56842: 실행 후 지연된 프록시 및 프록시 팩토리가 누락됨 `setup:di:compile`

ACSD-56842 패치는 실행 후 지연된 프록시 및 프록시 팩토리가 누락되는 문제를 수정합니다 `setup:di:compile`. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46이 설치되었습니다. 패치 ID는 ACSD-56842입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

실행 후 지연된 프록시 및 프록시 팩토리가 누락되었습니다. `setup:di:compile`.

<u>재현 단계</u>:

1. (이)라는 이름의 사용자 정의 모듈 만들기 *Magento_사용자 정의 모듈*.
1. 다음에서 *[!UICONTROL etc]* 모듈의 폴더, 만들기 `di.xml` 다음 내용으로:

   ```xml
    <?xml version="1.0"?>
     <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
        <type name="Magento\Catalog\Model\ProductLink\CollectionProvider">
           <arguments>
              <argument name="providers" xsi:type="array">
                 <item name="crosssell" xsi:type="object">
                      Magento\Catalog\Model\ProductLink\CollectionProvider\Crosssell\Proxy
                 </item>
                   <item name="upsell" xsi:type="object">Magento\Catalog\Model\ProductLink\CollectionProvider\Upsell\Proxy</item>
                     <item name="related" xsi:type="object">Magento\Catalog\Model\ProductLink\CollectionProvider\Related\Proxy</item>
              </argument>
           </arguments>
         </type>
            <type name="Magento\Catalog\Model\Product">
               <arguments>
                  <argument name="catalogProductStatus" xsi:type="object">
                   Magento\Catalog\Model\Product\Attribute\Source\Status\Proxy
                  </argument>
                   <argument name="productLink" xsi:type="object">
                     Magento\Catalog\Model\Product\Link\Proxy
                   </argument>
               </arguments>
             </type>
     </config>
   ```

1. 설정 [!UICONTROL Production] 모드: `bin/magento deploy:mode:set production`.
1. magento 루트에서 생성된 폴더를 삭제합니다.
1. 명령 실행 `bin/magento setup:di:compile`.
1. 생성된 폴더를 확인합니다.

<u>예상 결과</u>:

* 컴파일 후 프록시 파일을 만들었습니다.
* 컴파일 후 팩터리 파일이 성공적으로 만들어졌습니다.

<u>실제 결과</u>:

생성된 폴더에서 줄 바꿈 없이 지정된 프록시 인수에 대해 프록시 파일이 생성되며 줄 바꿈을 통해 지정된 인수에 대해서는 생성되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
