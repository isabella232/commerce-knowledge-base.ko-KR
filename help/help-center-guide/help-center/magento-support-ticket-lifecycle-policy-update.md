---
title: Adobe Commerce 지원 티켓 라이프사이클 정책 업데이트
description: 이 문서에서는 Adobe Commerce 지원 티켓 라이프사이클 정책 업데이트에 대한 정보를 제공합니다.
exl-id: c3fbcb4a-107f-48b3-afed-b9a0c5d0425c
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 1%

---

# Adobe Commerce 지원 티켓 라이프사이클 정책 업데이트

이 문서에서는 Adobe Commerce 지원 티켓 라이프사이클 정책 업데이트에 대한 정보를 제공합니다.

다음 표는 업데이트된 시나리오를 보여 줍니다. 아래 섹션에서 각 시나리오에 대한 세부 정보를 찾을 수 있습니다.

<table>
 <tbody>
 <tr>
 <td class="wysiwyg-text-align-center"> </td>
 <td class="wysiwyg-text-align-center"><strong>티켓 상태</strong></td>
 <td class="wysiwyg-text-align-center"><strong>해결 일 수</strong></td>
 <td class="wysiwyg-text-align-center"><strong>마감일: "종료"</strong></td>
 <td class="wysiwyg-text-align-center"><strong>알림 시간</strong></td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>엔지니어가 솔루션 제공</strong></td>
 <td class="wysiwyg-text-align-center">"답변 대기 중"</td>
 <td class="wysiwyg-text-align-center">3</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">3일 및 6일</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>고객으로부터 정보 대기 중</strong></td>
 <td class="wysiwyg-text-align-center">"답변 대기 중"</td>
 <td class="wysiwyg-text-align-center">해당 사항 없음</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">1, 3 및 6일</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>고객이 "해결됨"으로 설정하거나 엔지니어가 "해결됨"으로 설정하도록 요청합니다.</strong></td>
 <td class="wysiwyg-text-align-center">"해결됨"</td>
 <td class="wysiwyg-text-align-center">즉시</td>
 <td class="wysiwyg-text-align-center">1</td>
 <td class="wysiwyg-text-align-center">1일</td>
 </tr>
 </tbody>
 </table>

## 시나리오 세부 정보

### 엔지니어가 솔루션을 제공하는 경우

1. 고객에게 솔루션이 제공되면 엔지니어는 티켓 상태를 &quot;회신 대기 중&quot;으로 설정합니다.
1. 상태가 &quot;회신 대기 중&quot;으로 변경된 후 3일 동안 고객으로부터 응답이 없는 경우 티켓이 &quot;해결됨&quot;으로 이동되고 고객에게 알립니다.
1. 상태가 &quot;회신 대기 중&quot;으로 변경된 후 6일 동안 고객으로부터 응답이 없는 경우 - 티켓이 닫히고 고객에게 알립니다.

### 고객으로부터 추가 정보가 필요한 경우

1. 고객의 업데이트가 필요한 경우 엔지니어는 티켓을 &quot;회신 대기 중&quot;으로 설정합니다.
1. 고객에게 후속 조치를 요청하는 1일과 3일에 알림이 전송됩니다.
1. 상태가 &quot;회신 대기 중&quot;으로 변경된 후 6일 동안 고객으로부터 응답이 없는 경우 - 티켓이 닫히고 고객에게 알립니다.

### 고객이 &quot;해결됨&quot;으로 설정한 티켓

고객이 티켓을 &#39;해결&#39;로 설정하면 하루 만에 마감돼 고객에게 알린다.

### 고객이 지원팀에 티켓 닫기를 지시함

고객이 Adobe Commerce 지원 팀에 티켓을 닫으라고 지시하면 하루 만에 닫히고 고객에게 알립니다.

## 관련 읽기

* [지원 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)
* [Adobe Commerce 도움말 센터 시작 페이지에 &quot;티켓 제출&quot; 링크가 표시되지 않음](/help/help-center-guide/help-center/magento-help-center-user-guide.md#no-submit-link)
* [티켓 제출 양식: 판매자가 조직 드롭다운에 표시되지 않음](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)
