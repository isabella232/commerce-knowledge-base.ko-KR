---
title: 데이터 불일치 진단
description: 이 문서에서는 MBI(Magento Business Intelligence) 보고서와 쿼리 또는 타사 보고서 간 불일치를 해결하는 방법을 제공합니다.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 데이터 불일치 진단

이 문서에서는 MBI(Magento Business Intelligence) 보고서와 쿼리 또는 타사 보고서 간 불일치를 해결하는 방법을 제공합니다.

분석의 복잡성에 따라 해당 MBI 보고서를 생성하려면 플랫폼의 여러 다른 패싯에 익숙해야 할 수 있습니다. 이 체크리스트 및 관련 링크는 모든 불일치의 출처를 식별할 수 있도록 보고서 이면의 논리를 이해하는 데 도움이 됩니다.

1. 팀의 다른 구성원이 보고서를 만든 경우 먼저 분석의 목적과 매개 변수를 확인합니다.
1. 쿼리, 서드파티 보고 도구 또는 수식을 기반으로 MBI 보고서와 비교할 예상 데이터 포인트를 생성합니다.
1. 검토 및 확인 [지표](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html) Report Builder의 지표 링크에서 정의하거나 [시스템 요약](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary) 탭:
   * 데이터 테이블
   * 작업
   * 피연산자 열, 파생된 경우 해당 계산 포함(시스템 요약을 통해)
   * 타임스탬프
   * 구독 지표의 경우: 시작 및 종료 날짜
   * 필터(다음 중 하나에 포함된 것을 포함한다) [필터 세트](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html) 적용됨
1. 보고서에서 다른 데이터 조작을 검토하고 확인합니다.
   * 계산된 공식
   * [그룹화](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [관점](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [시간 옵션](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * 대상 [집단 분석](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): 집단 날짜
   * 대상 [집단 분석](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): 집단 관점
1. 불일치에 최근 데이터가 포함된 경우 **업데이트 세부 정보** 섹션에 있는 마지막 항목이 될 필요가 없습니다.
1. 분석에 사용된 지표가 해당 테이블에서 행이 삭제된 데이터베이스의 테이블에 작성되어 있는 경우 MBI 지원 팀에 테이블이 삭제된 행에 대해 검사되고 있는지, 다시 검사하고 를 실행하는 빈도도 확인하시기 바랍니다. [복제 방법](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) 테이블로요.
1. 마찬가지로, 행에 추가한 후 분석에 사용된 열을 수정할 수 있는 경우 이 열이 추가되었는지 지원으로 확인합니다 [수정을 확인했습니다.](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html): 및 재검사 빈도입니다.

**아직도 난처해?** 걱정하지 마세요. 우린 도우러 왔어요. 다음을 사용하여 요청 보내기 [이 지침](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).
