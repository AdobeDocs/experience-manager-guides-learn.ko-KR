---
title: AEM Guides 편집기 구성
description: 새 AEM Guides 편집기에 대한 JSON 구성 사용자 지정 및 UI 구성 전환.
source-git-commit: ec6f5685d690e53e5c6eb29d6b61436833f62c68
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# 개요

이전 UI에서 새 AEM Guides UI로 마이그레이션할 때 **ui_config** 업데이트는 보다 유연하고 모듈식 UI 구성으로 변환되어야 합니다. 이 프레임워크를 사용하면 **editor_toolbar** 및 [기타 도구 모음](/help/courses/course-3/conver-ui-config.md#editing-json-for-different-screens)에 변경 내용을 원활하게 적용할 수 있습니다. 이 프로세스는 애플리케이션에서 다른 보기 및 위젯을 수정하는 것을 지원합니다.


## 다른 화면에 대한 JSON 편집

다양한 화면 및 위젯에 대한 XML 편집기 UI 구성 섹션에 JSON 파일을 추가할 수 있습니다. 다음은 널리 사용되는 위젯과 해당 ID의 목록입니다.

1. [editor_toolbar](assets/toolbars/editor_toolbar.json): 파일 및 콘텐츠 작업으로 구성된 Webeditor 도구 모음
1. [editor_tab_bar](assets/toolbars/editor_tab_bar.json): 웹 편집기 내에서 열린 파일의 탭 보기이며, 열린 파일에 대해 수행할 수 있는 작업이 있습니다.
1. [file_mode_switcher](assets/toolbars/file_mode_switcher.json): 웨비터 내에서 열린 파일에 대해 사용 가능한 다양한 모드(작성자, 소스, 미리보기) 간을 전환하는 데 도움이 됩니다.

   ![editor_toolbar](images/reuse/editor_toolbar.png)

1. [map_console_navigation_bar](assets/toolbars/map_console_navigation_bar.json): 맵 콘솔에 열려 있는 맵의 정보 표시줄입니다. 맵을 변경할 수 있고 설정에 액세스할 수 있습니다.
1. [map_console_action_bar](assets/toolbars/map_console_action_bar.json): [출력 사전 설정], [기준 요소], [변환] 및 [보고서]와 같은 맵 콘솔 항목의 작업 표시줄이며 각 작업 단추와 함께 관련 정보를 제공합니다.

   ![map_console](images/reuse/map_console.png)

1. [home_navigation_bar](assets/toolbars/home_navigation_bar.json): 선택한 폴더 프로필과 함께 시작 메시지가 표시되는 안내 홈 페이지의 헤더 막대

   ![home_navigation_bar](images/reuse/home_navigation_bar.png)

<br>

## 각 JSON의 일반 구조

각 JSON은 일관된 구조를 따릅니다.

1. **id**: 구성 요소를 사용자 지정하는 위젯을 지정합니다.
1. **targetEditor**: 편집기 및 모드 속성을 사용하여 단추를 표시하거나 숨길 시기를 정의합니다.

   현재 시스템에 이러한 **editor** 및 **mode**&#x200B;이(가) 있습니다.

   **editor**: ditamap, bookmap, subjectScheme, xml, css, translation, preset, pdf_preset

   **모드**: 작성자, 원본, 미리 보기, 목차, 분할

   참고: 목차 모드는 레이아웃 보기에 적용됩니다.

1. **target**: 새 구성 요소를 추가할 위치를 지정합니다. 고유한 식별을 위해 키-값 쌍 또는 인덱스를 사용합니다. 보기 상태는 다음과 같습니다.

   * **추가**: 끝에 를 추가합니다.

   * **prepend**: 시작 부분에 추가하십시오.

   * **바꾸기**: 기존 구성 요소를 바꿉니다.

예제 JSON 구조:

```json
{
  "id" : "editor_toolbar",
  "view": {
    "items": [
      {
        ...,
        "targetEditor": {
          "mode": [
            "preview"
          ],
          "editor": [
            "xml"
          ]
        },
        "target": {
          "key": "label",
          "value": "Table",
          "viewState": "prepend"
        },
        ...
      },
    ]
  }
}
```

<br>

## 예

다음은 편집기 도구 모음에서 단추를 추가, 삭제 또는 바꾸는 방법에 대한 예입니다.

### 단추 추가

미리 보기 모드에서만 볼 수 있는 간단한 테이블을 추가하려면 **editor_toolbar**&#x200B;에 새 단추 **사용자 지정 테이블 삽입**&#x200B;을(를) 추가합니다.

```json
{
  "id": "editor_toolbar",
  "view": {
    "items": [
      {
        "icon": "table",
        "title": "Insert Custom Table",
        "on-click": {
          "name": "$$AUTHOR_INSERT_ELEMENT",
          "args": [
            "simpletable",
            "table",
            "choicetable"
          ]
        },
        "key": "$$AUTHOR_INSERT_ELEMENT",
        "targetEditor": {
          "mode": [
            "preview"
          ],
        },
        "target": {
          "key": "label",
          "value": "Table",
          "viewState": "prepend"
        }
      }
    ]
  }
}
```

![사용자 지정 테이블 삽입](images/reuse/insert-custom-table.png)

### 단추 삭제

도구 모음에서 단추 삭제 여기에서는 편집기 도구 모음에서 이미지 추가 단추를 제거하겠습니다.

```json
{
  "id": "editor_toolbar",
  "view": {
    "items": [
      {
        "hide": true,
        "target": {
          "key": "label",
          "value": "Image",
          "viewState": "replace"
        }
      }
    ]
  }
}
```

### 단추 바꾸기

도구 모음의 **멀티미디어** 단추를 작성자 모드에서만 볼 수 있는 **Youtube** 링크 삽입 단추로 바꿉니다.

```json
{
  "id": "editor_toolbar",
  "view": {
    "items": [
      {
        "icon": "s2youtube",
        "title": "Youtube",
        "on-click": {
          "name": "$$AUTHOR_INSERT_ELEMENT",
          "args": "<object data='http://youtube.com'></object>"
        },
        "targetEditor": {
          "mode": [
            "author"
          ]
        },
        "target": {
          "key": "elementId",
          "value": "toolbar-multimedia",
          "viewState": "replace"
        }
      }
    ]
  }
}
```

![Youtube 단추](images/reuse/youtube-button.png)

<br>

## 사용자 지정된 JSON을 업로드하는 방법

1. **XML 편집기 구성** 탭의 상단 표시줄에서 **편집**&#x200B;을 클릭합니다.
1. 이제 **XML 편집기 UI 구성** 하위 섹션에서 **업로드** 단추를 볼 수 있습니다.

   ![업로드 단추](images/reuse/ui-config-upload.png){width="400" height="150"}

1. 을 클릭하고 수정된 JSON을 업로드할 수 있습니다. (업로드할 JSON의 이름은 사용자 지정 중인 위젯 ID와 동일해야 함)
1. 업로드한 후에는 상단 표시줄의 **저장**&#x200B;을 누르십시오.

   업로드된 각 파일에 대해 UI에서 JSON을 **삭제**&#x200B;하여 해당 사용자 지정 항목을 제거하거나 **다운로드**&#x200B;하여 다시 보거나 수정할 수도 있습니다.

   ![다운로드 단추](images/reuse/download-delete-json.png){width="400" height="150"}

<br>


## 사용자 지정된 CSS를 업로드하는 방법

UI에서 사용자 정의 추가 단추 또는 이미 존재하는 위젯 또는 단추의 모양과 느낌을 사용자 정의하기 위해 css를 추가할 수도 있습니다.

새로 추가된 사용자 지정 단추의 경우 JSON 내의 사용자 지정 단추 또는 구성 요소에 **extraclass**&#x200B;를 추가합니다.
이전 클래스의 경우 요소를 검사하고 기존 클래스를 수정할 수도 있습니다.

```json
{
  "icon": "table",
  "title": "Insert Custom Table",
  "extraclass": "custom-css",
  "key": "$$AUTHOR_INSERT_ELEMENT",
  "targetEditor": {
    "mode": [
      "preview"
    ],
  },
  "target": {
    "key": "label",
    "value": "Table",
    "viewState": "prepend"
  }
}
```

1. **XML 편집기 구성** 탭의 상단 표시줄에서 **편집**&#x200B;을 클릭합니다.
1. 이제 **XML 편집기 페이지 레이아웃** 하위 섹션에서 **업로드** 단추를 볼 수 있습니다.

   ![업로드 단추](images/reuse/page-layout-upload.png){width="400" height="150"}

1. 을(를) 클릭하고 수정된 css를 업로드할 수 있습니다. (css 파일만 지원됨)
1. 업로드한 후에는 상단 표시줄의 **저장**&#x200B;을 누르십시오.

   업로드된 각 파일에 대해 css를 **삭제**&#x200B;하여 UI에서 해당 사용자 지정 항목을 제거하거나 **다운로드**&#x200B;하여 다시 보거나 수정할 수도 있습니다.

   ![다운로드 단추](images/reuse/download-delete-css.png){width="400" height="150"}


<br>

### 단추 css 맞춤화 예제

여기서는 **editor_toolbar**&#x200B;에 새 단추 **사용자 지정 테이블 삽입**&#x200B;을 추가하여 미리 보기 모드에서만 볼 수 있는 간단한 테이블을 추가하고 사용자 지정 css를 적용합니다.
이 css는 버튼의 배경과 제목의 글꼴 크기를 수정합니다.

![CSS 예제](images/reuse/css-customization.png)


```css
#editor_toolbar {
  .custom-css {
    background-color: burlywood;
    font-size: 2rem;  
  }
}
```

```json
{
  "id": "editor_toolbar",
  "view": {
    "items": [
      {
        "icon": "table",
        "title": "Insert Custom Table",
        "extraclass": "custom-css",
        ...
      }
    ]
  }
}
```

<br>

## ui 구성을 모듈식 Json으로 변환하는 단계

1. 탐색 화면에서 [!UICONTROL **도구**] 아이콘을 클릭합니다.

   ![도구 아이콘](images/reuse/tools.png)

1. 왼쪽 패널에서 **안내서**&#x200B;를 선택합니다.

1. [!UICONTROL **폴더 프로필**] 타일을 클릭합니다.

   ![폴더 프로필](images/reuse/folder-profiles-tile.png)

1. 폴더 프로필을 선택합니다.

1. [!UICONTROL **XML 편집기 구성**] 탭을 클릭합니다.

1. **UI 구성을 JSON으로 변환** 단추를 클릭할 수 있습니다. **ui_config**&#x200B;에서 수행된 변경 내용이 포함된 **editor_toolbar** 및 **map_console_action_bar** json이 생성됩니다.

   ![UI 구성을 JSON으로 변환](images/reuse/convert-ui-config-json.png)

1. [편집기 도구 모음](assets/editor_toolbar.json) 및 [맵 콘솔 작업 모음](assets/map_console_action_bar.json)에 대해 샘플 생성 작업을 확인할 수 있습니다.


>[!NOTE]
>
>**도구 모음** 및 **topbar** 섹션에 대한 변경 사항이 편집기 페이지에서 볼 수 있는 **editor_toolbar** json에 추가됩니다. **ui_config**&#x200B;의 사전 설정 또는 번역 관련 단추에 대한 변경 사항이 맵 콘솔 페이지에서 볼 수 있는 **map_console_action_bar** json에 추가됩니다.
