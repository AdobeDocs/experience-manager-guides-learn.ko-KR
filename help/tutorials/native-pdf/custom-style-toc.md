---
title: 기본 PDF 게시 기능 | 목차 항목 및 주제 컨텐츠에 사용자 지정 스타일 적용
description: 스타일시트를 만들고 내용에 대한 스타일을 만드는 방법을 알아봅니다.
source-git-commit: 09918abbdade934468dea1c55d0ca2cd60622b35
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# 목차 항목 및 주제 컨텐츠에 사용자 지정 스타일 적용

때로는 TOC 항목 또는 특정 주제에 사용자 지정 스타일을 적용할 수 있습니다. 이를 위해서는 `outputclass` 속성을 `<topicref>` DITA 맵에 있는 요소. 또한 전체 주제에 사용자 지정 형식을 적용하려는 경우 CSS에서 속성의 스타일 정의를 확장하여 이를 구현할 수도 있습니다.

검토를 위해 보낼 새 항목의 예를 살펴보겠습니다. 업데이트된 항목을 쉽게 식별하려면 `outputclass` 속성을 `<topicref>` 요소를 DITA 맵에 넣은 다음 CSS에서 해당 요소에 대한 사용자 지정 스타일을 정의합니다.

다음 예에서 *비행의 역사* 주제가 지정되었습니다 `outputclass` 값이 인 속성 `new-topic`.

<img src="./assets/new-topic-attribute-in-map.png" width="500">

의 클래스 정의입니다. `new-topic` css에서 다음 항목에 대한 스타일을 정의할 수 있습니다.
* TOC 또는 미니 목차의 기본 항목
* 기본 컨텐츠에서 항목의 제목입니다
* 제목을 포함하여 항목의 전체 컨텐츠입니다

CSS에서 이러한 각 시나리오를 정의할 수 있는지 보겠습니다. 다음 CSS 정의에서 `new-topic` 클래스, 텍스트 색상이 변경되었습니다.

```css
…
.new-topic {
  color: #CC5309
}
…
```

이 정의는 목차에 있는 텍스트 색상과 주제 제목을 제어합니다. 다음 PDF 출력은 TOC 항목에 적용된 다른 색상을 보여줍니다.

<img src="./assets/pdf-output-toc-entry.jpg" width="500">

주제 제목도 동일한 색상을 사용하여 스타일이 지정됩니다.

<img src="./assets/pdf-output-topic-title.jpg" width="500">

목차 항목과 주제 제목에 다른 스타일을 포함하려면 아래 표시된 대로 별도로 정의할 수 있습니다.

```css
...
/*for styling TOC entry */
.new-topic {
  color: #CC3509
}

/* for styling topic's title */
.new-topic.title {
  color: #092ACC
}
...
```

마지막으로 주제 내의 전체 컨텐츠에 스타일을 적용할 수도 있습니다. 이렇게 하려면 접미사 &quot;`-content`&quot; 값을 클래스 이름에 추가합니다. 다음 예에서는 항목의 전체 컨텐츠에 변경 표시줄이 추가되었습니다.

```css
...
/* for styling the topic's content */
.new-topic-content {
  -ro-change-bar-color: #A609CC;
}
...
```

위의 스타일 속성을 사용하여 변경 막대가 페이지의 왼쪽에 추가됩니다 *비행사* 아래와 같이 주제를 지정합니다.

<img src="./assets/pdf-output-topic-content.jpg" width="500">


