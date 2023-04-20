---
title: 안내선 편집기에 사용자 지정 스타일 추가
description: 사용자 정의 스타일을 추가하여 안내서 웨비더의 모양과 느낌을 변경하는 방법을 알아봅니다.
source-git-commit: 9e7d5bb4c8f6c6ebe21bfcebdd7d2e13971b8df2
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 안내선 편집기에 사용자 지정 스타일 추가

이 문서에서는 사용자 지정 스타일을 추가하여 웨비나 기본 모양 및 느낌을 변경하는 방법을 알아봅니다.

여기에는 다음 단계가 포함됩니다.
- 폴더 프로필 XML 편집기 구성을 통해 사용자 지정 스타일 추가
- Webeditor에서 각 폴더 프로필을 선택하고 변경 사항을 테스트합니다


## 예를 들어 구현

편집기에서 몇 가지 스타일 측면이 있는 별도의 블록으로 짧은 설명 및 제목을 표시하려는 예를 사용하여 이를 이해하겠습니다.

![사용자 지정 스타일로 웨비나 미리 보기](../../../assets/authoring/webeditor-customstyles-preview.png)


## 이 구현


### 폴더 프로필에 사용자 지정 CSS 추가

폴더 프로필을 사용하여 *css_layout.css* &quot;XML 편집기 구성&quot; 탭에서 사용자 지정 스타일이 있는 CSS를 추가합니다.

[폴더 프로필 및 CSS 템플릿 레이아웃 구성에 대한 자세한 내용을 보려면 이 링크를 사용하십시오](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/videos/advanced-user-guide/editor-configuration.html?lang=en#customize-the-css-template-layout)

웹 편집기에서 위의 스타일을 설정하려면 다음을 사용하십시오.
- 사용 [css_layout.css](../../../assets/authoring/webeditor-customstyles-css_layout.css) 원하는 폴더 프로필에 업로드합니다
- 첨부된 패키지 설치 [webeditor-styles-resources.zip](../../../assets/authoring/webeditor-styles-resources.zip) AEM 패키지 관리자를 사용하여 위의 CSS 파일에 사용되는 리소스를 설치합니다.

```
This will install the resources at path "/content/dam/resources" which will include sub-folders "fonts" and "images"
```


### 테스트

- 웹 편집기 열기
- 사용자 환경 설정에서 사용자 지정 스타일을 추가한 폴더 프로필을 선택합니다. 글로벌 프로필에 추가했다면 이미 해당 프로필을 사용하고 있을 수 있습니다.
- 항목을 열면 편집 영역에 사용자 지정 UI가 있어야 합니다

```
Please note this is compatible to AEM Guides version 4.2 and AEM Guides cloud version 2303 (March)
```


## 참조

또한, [웨비더에 대한 전문가 세션](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/knowledge-base/expert-session/webbased-authoring-jan2023.html?lang=en)