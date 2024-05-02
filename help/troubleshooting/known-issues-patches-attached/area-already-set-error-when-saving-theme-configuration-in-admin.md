---
title: 책임자에 테마 구성을 저장할 때 "영역이 이미 설정됨" 오류 발생"
description: 이 문서에서는 Commerce 관리에서 기본 스토어 보기에 대한 테마를 설정하려고 할 때 *"영역이 이미 설정됨"* 오류 메시지를 가져오는 것과 관련된 클라우드 인프라 2.2.4의 알려진 Adobe Commerce 문제에 대한 패치를 제공합니다.
exl-id: c4e34a73-b774-4447-ba8e-aaf208ad54c5
feature: Admin Workspace, Configuration, Themes
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 관리에 테마 구성을 저장할 때 &quot;영역이 이미 설정됨&quot; 오류 발생

이 문서에서는 가져오기와 관련된 알려진 Adobe Commerce on cloud infrastructure 2.2.4 문제에 대한 패치를 제공합니다. *&quot;영역이 이미 설정됨&quot;* Commerce 관리에서 기본 스토어 보기에 대한 테마를 설정하려고 할 때 오류 메시지가 표시됩니다.

## 문제

&quot; *이 구성을 저장하는 동안 문제가 발생했습니다. 영역이 이미 설정되었습니다.* &quot;기본 스토어 보기에 대한 테마를 설정하려고 할 때 오류 메시지가 표시됩니다.

<u>재현 단계</u>:

1. Commerce 관리자에 로그인합니다.
1. 다음으로 이동 **콘텐츠** > **디자인** > **구성**.
1. 구성 범위를 다음으로 설정 *기본 스토어 보기*.
1. 에서 테마 변경 **적용된 테마** 드롭다운. 예: 부터 *Luma* 끝 *비어 있음.*
1. 클릭 **구성 저장**.

<u>예상 결과</u>: 선택한 테마가 기본 스토어 보기에 적용됩니다.

<u>실제 결과</u> : 테마가 적용되지 않음, *&quot;이 구성을 저장하는 동안 문제가 발생했습니다. 영역이 이미 설정되었습니다.&quot;* 오류 메시지가 표시됩니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 다음 링크를 클릭하거나 문서 끝까지 스크롤하여 첨부 파일을 클릭하십시오.

[MDVA-11106\_EE\_2.2.4\_v1.composer.patch 다운로드](assets/MDVA-11106_EE_2.2.4_v1.composer.patch.zip)

## 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce 2.2.4

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 클라우드 인프라의 Adobe Commerce 2.0.X
* 클라우드 인프라의 Adobe Commerce 2.1.X
* 클라우드 인프라 2.2.0의 Adobe Commerce - 2.2.5
* Adobe Commerce 온-프레미스 2.0.X
* Adobe Commerce 온-프레미스 2.1.X
* Adobe Commerce 온-프레미스 2.2.0 - 2.2.5

## 패치 적용 방법

자세한 내용은 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 을 참조하십시오.

## 첨부 파일
