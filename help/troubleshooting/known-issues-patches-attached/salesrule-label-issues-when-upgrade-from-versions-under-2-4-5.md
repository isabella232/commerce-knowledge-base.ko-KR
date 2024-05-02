---
title: '''[!UICONTROL salesRule] 버전 &lt; 2.4.5''에서 업그레이드 시 레이블 문제'
description: '** 처리를 위해 패치 적용[!UICONTROL salesRule]Adobe Commerce 버전 &lt; 2.4.5에서 업그레이드할 때 ** 문제가 발생합니다.'
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# **[!UICONTROL salesRule]** 버전 2.4.5에서 업그레이드 시 레이블 문제 발생

다음 **[!UICONTROL salesRule]** 레이블 스테이징 기능은 Adobe Commerce에 도입되었습니다. [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). 이 변경 사항으로 인해 Adobe Commerce &lt; 2.4.5에서 버전 >= 2.4.5로 업그레이드할 때 문제가 발생할 수 있습니다. 업그레이드 후 다음과 같은 가능성이 있습니다. **[!UICONTROL salesRule]** 레이블이 일치하지 않습니다. 문제를 해결하려면 최신 Adobe Commerce 버전으로 업그레이드 한 직후에 패치를 적용해야 합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce &lt; 2.4.5

## 패치

첨부된 다음 패치를 사용합니다.

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## 패치 적용 방법

1. 의 단계를 따릅니다. [업그레이드 수행](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) Commerce 안내서에서 확인할 수 있습니다.
1. 앞에 첨부된 패치를 적용합니다. **[!UICONTROL Update metadata]** 단계.
(다음을 완료한 후 패치를 적용할 수도 있습니다.) **[!UICONTROL Update metadata]** 단계는 실행되어야 합니다. `bin/magento setup:upgrade` 다시 한 번).
1. 의 나머지 단계를 계속 진행합니다. [업그레이드 수행](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
