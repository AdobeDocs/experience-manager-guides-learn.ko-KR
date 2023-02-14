---
title: 기본 PDF 게시 기능 | 목차 항목 및 주제 컨텐츠에 사용자 지정 스타일 적용
description: 스타일시트를 만들고 내용에 대한 스타일을 만드는 방법을 알아봅니다.
source-git-commit: fbb81704ea8d9d2793b066fa159b405460fa1dcf
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---


# PDF 출력에 사용자 지정 책갈피 추가

일반적으로 DITA 맵의 TOC는 최종 PDF 출력에서 책갈피로 복제됩니다. 이 목차는 DITA 맵의 주제 또는 섹션 제목에서 만들어집니다. 간편한 탐색을 위해 PDF 출력의 특정 콘텐츠에 사용자 지정 책갈피를 추가할 수 있습니다. 이를 위해서는 `outputclass` 속성에 대한 속성 및 다음 속성을 요소에 적용합니다.

`bookmark-level: 3`

여기, `bookmark-level` 는 속성 및 번호입니다 `3` 책갈피가 추가되는 책갈피 계층의 수준을 나타내는 값입니다. 다음 예제에서는 첫 번째 수준 항목인 &quot;연락처&quot; 에는 &quot;연락처 목록&quot;이라는 테이블이 있습니다. 여기에서 `outputclass` 값이 인 속성 `custom-bookmark`.

<img src="./assets/custom-bookmark-attribute.png" width="500">

다음에 대한 다음 정의 `custom-bookmark` 클래스는 CSS 파일에 추가됩니다.

```css
…
/*Adding a custom bookmark*/
.custom-bookmark{
    bookmark-level: 2
}
…
```

PDF 출력에서 *연락처 목록* 표는 아래와 같이 PDF 책갈피 목록의 두 번째 수준에 추가됩니다.

<img src="./assets/custom-bookmark-in-pdf-output.png" width="500">
