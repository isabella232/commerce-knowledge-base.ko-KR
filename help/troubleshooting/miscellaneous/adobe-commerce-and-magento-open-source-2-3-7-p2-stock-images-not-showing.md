---
title: 스톡 이미지가 표시되지 않음, Adobe Commerce 및 Magento Open Source 2.3.7-p2
description: 이 문서에서는 파일 시스템 디렉토리 'pub/media' 또는 'pub/media/catalog'에 업로드된 Adobe 스톡 이미지가 미디어 갤러리 UI에 표시되지 않는 문제에 대한 해결 방법을 제공합니다. 이는 이미지가 허용된 미디어 갤러리 디렉터리 외부에 있기 때문입니다. 이러한 이미지를 표시하려면 파일 시스템에서 이미지를 삭제하고 허용된 Media Gallery 디렉터리로 다시 업로드해야 합니다.
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# 스톡 이미지가 표시되지 않음, Adobe Commerce 및 Magento Open Source 2.3.7-p2

이 문서에서는 파일 시스템 디렉터리에 업로드된 Adobe 스톡 이미지에 대한 해결 방법을 제공합니다 `pub/media` 또는 `pub/media/catalog` 미디어 갤러리 UI에 를 표시하지 않습니다. 이는 이미지가 허용된 미디어 갤러리 디렉터리 외부에 있기 때문입니다. 이러한 이미지를 표시하려면 파일 시스템에서 이미지를 삭제하고 허용된 Media Gallery 디렉터리로 다시 업로드해야 합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 및 Magento Open Source 2.3.7-p2


## 문제

판매자는 Adobe Stock 이미지를 미디어 갤러리의 스토리지 루트에 업로드할 수 있지만 이러한 이미지는 UI에 표시되지 않고 업로드되지 않은 것처럼 표시됩니다. 이는 Media Gallery UI에서 사용할 수 없지만 파일 시스템에 이미지가 이미 업로드되어 있음을 시스템에서 인식하기 때문입니다. 이것은 판매자가 이미지를 로 업로드하면 `pub/media` 또는 `pub/media/catalog`즉, 해당 이미지는 파일 시스템에서 직접 삭제될 때까지 사용할 수 없습니다.

<u>재현 단계</u>

1. 유효한 API 키로 Adobe Stock을 활성화합니다.
1. 미디어 갤러리 열기(**카탈로그** > **카테고리** > **콘텐츠** 섹션 > 클릭 **갤러리에서 선택**).
1. 클릭 **Adobe Stock 검색**.
1. 이미지를 선택합니다. 클릭 **미리 보기 저장**. 이미지를 표시하려면 Adobe Stock 그리드를 재설정해야 할 수 있습니다.

<u>예상 결과</u>:

이미지가 표시됩니다.

<u>실제 결과</u>:

오류 메시지가 표시됩니다. *이미지를 찾을 수 없습니다. 미디어 갤러리에서 이 이미지를 찾을 수 없습니다.*

## 원인

Adobe Stock을 통해 이미지를 Media Gallery 스토리지 루트에 업로드할 수 있습니다.

## 솔루션

미디어 갤러리 스토리지 루트의 하위 디렉토리를 선택합니다(제외). **저장소 루트** > **카탈로그**)를 클릭하여 Adobe Stock 이미지를 업로드하십시오.
에서 업로드된 Adobe Stock 이미지 삭제 `pub/media` 및 `pub/media/catalog` Adobe Commerce 파일 시스템의 폴더와 이미지를 허용된 모든 미디어 갤러리 스토리지 루트 하위 디렉토리에 대신 업로드합니다(제외) **저장소 루트** > **카탈로그**).

## 관련 읽기

* [미디어 스토리지](https://docs.magento.com/user-guide/v2.3/cms/media-storage.html) 사용 안내서에서 참조하십시오.
