---
title: 기본 PDF 게시 기능 | 각주에서 사용자 지정 스타일 사용
description: 각주의 숫자에 스타일을 적용하는 방법에 대해 알아봅니다.
exl-id: f1068f2f-2ace-4bdb-b5a4-46b03d4e43d6
source-git-commit: 7b48633ef2418fa7c91842a8d2c2a4177017ef58
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# 각주에서 사용자 정의 스타일 사용

각주는 지정된 텍스트 부분에 대한 참조를 설명하거나 인용하는 페이지 하단에 배치됩니다.

항목 콘텐츠에 있는 각주 호출의 숫자와 페이지 하단에 있는 각주 마커의 스타일을 지정할 수 있습니다. 예를 들어 숫자 주위에 대괄호를 추가하거나 색상을 변경할 수 있습니다. 이러한 스타일을 사용하면 문서의 각주를 쉽게 식별할 수 있습니다.

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

주어진 예에서 각주 호출 및 마커 전후에 괄호가 추가됩니다.

* 의 content 속성을 사용하여 접두사 &quot;(&quot; 및 접미사 &quot;)&quot;를 추가합니다. `footnote-call` 스타일 : 주제 콘텐츠의 각주 번호 주위에 대괄호를 추가합니다.
* 의 content 속성을 사용하여 접두사 &quot;(&quot; 및 접미사 &quot;)&quot;를 추가합니다. `footnote-marker` 스타일 : 페이지 하단에 각주 번호 주위에 대괄호를 추가합니다.

<img src="./assets/pdf-output-footer-numbers.png" alt="PDF 출력의 바닥글" width="500">
