---
title: Magento Order Management 제거 방법(MOM)
description: 이 문서에서는 MOM(Magento Order Management) 시스템을 제거하는 방법에 대해 설명합니다.
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Magento Order Management 제거 방법(MOM)

1. 의 단계에 따라 MOM 통합을 비활성화합니다. [통합 비활성화 또는 활성화](/docs/commerce-admin/systems/integrations/mcom.html#disable-or-enable-the-integration).
1. 의 단계에 따라 MOM 모듈을 비활성화합니다. [모듈 제거](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. 전체 주문 데이터를 추출하기 위해 API를 제공합니다. 다음을 검토하여 자세한 내용을 알아볼 수 있습니다. [저장소 주문](https://omsdocs.magento.com/specifications/#magento.sales.order_repository) Adobe 내 | 주문 정보(order_repository)를 다루는 Magento OMS 문서. 사용 [사양 섹션](https://omsdocs.magento.com/specifications/#services) Adobe 내 | 다른 API를 사용하여 다양한 정보 유형을 추출하도록 OMS 문서 Magento
