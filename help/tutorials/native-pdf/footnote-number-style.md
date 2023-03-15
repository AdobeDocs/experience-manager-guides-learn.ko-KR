---
title: 기본 PDF 게시 기능 | 각주에서 사용자 지정 스타일 사용
description: 각주에 있는 숫자에 스타일을 적용하는 방법을 알아봅니다.
source-git-commit: ef562c43f5b70d3fe425427108ad8277e1456f24
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# 각주에서 사용자 지정 스타일 사용

각주는 텍스트의 지정된 부분에 대한 참조를 언급하거나 인용하는 페이지 하단에 삽입되는 노트입니다.

주제 컨텐츠에 있는 각주 호출과 페이지 하단에 있는 각주 마커의 스타일을 지정할 수 있습니다. 예를 들어 숫자 주위에 대괄호를 추가하거나 색상을 변경할 수 있습니다. 이러한 스타일은 문서의 각주를 쉽게 식별하는 데 도움이 됩니다.

```css
...
.footnote::footnote-call { 
content: "(" counter(footnote, decimal) ")"; 
} 

.footnote::footnote-marker { 
content: "(" counter(footnote, decimal) ")"; 
} 

...
```

지정된 예제에서 각주 호출 및 마커의 앞과 뒤에 브래킷이 추가됩니다.

* 에서 컨텐츠 속성을 사용하여 접두사 &quot;(&quot; 및 접미사 &quot;)&quot;를 추가합니다. `footnote-call` 주제 컨텐츠의 각주 번호 주위에 대괄호를 추가하는 스타일.
* 에서 컨텐츠 속성을 사용하여 접두사 &quot;(&quot; 및 접미사 &quot;)&quot;를 추가합니다. `footnote-marker` 페이지 하단의 각주 번호 주위에 대괄호를 추가하는 스타일입니다.

<img src="./assets/pdf-output-footer-numbers.png" alt="PDF 출력의 바닥글" width="500">
