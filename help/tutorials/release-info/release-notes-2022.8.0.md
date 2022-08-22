---
title: 릴리스 노트 | Adobe Experience Manager 안내서 as a Cloud Service, 2022년 8월 릴리스
description: Adobe Experience Manager 안내서의 최신 릴리스 as a Cloud Service
source-git-commit: 7cc33e4621c2bfbf08a720f173e8e419c5424a6c
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 2%

---

# Adobe Experience Manager 안내서의 최신 릴리스 as a Cloud Service

## 최신 릴리스로 업그레이드

현재 Adobe Experience Manager 가이드를 as a Cloud Service(라고 함)로 업그레이드합니다 *AEM 안내서 as a Cloud Service*) 다음 단계를 수행하여 설정합니다.
1. Cloud Services의 Git 코드를 확인하고 업그레이드하려는 환경에 해당하는 Cloud Services 파이프라인에 구성된 분기로 전환합니다.
2. 업데이트 `<dox.version>` 속성 `/dox/dox.installer/pom.xml` Cloud Services Git 코드 파일을 2022.8.167에 추가합니다.
3. 변경 사항을 커밋하고 Cloud Services 파이프라인을 실행하여 AEM Guides as a Cloud Service 최신 릴리스로 업그레이드합니다.

## 호환성 매트릭스

이 섹션에는 AEM Guides as a Cloud Service 2022년 8월 릴리스에서 지원하는 소프트웨어 응용 프로그램의 호환성 매트릭스가 나와 있습니다.

### FrameMaker 및 FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 호환되지 않음 | 2020 업데이트 4 이상 |
|  |  |

*AEM에서 작성된 기준 및 조건은 2020.2년부터 MPS 릴리스에서 지원됩니다.

### 산소 커넥터

| AEM Guides as a Cloud Release | 산소 커넥터 창 | 산소 커넥터 Mac |
| --- | --- | --- |
| 2022.8.0 | 2.7.5 | 2.7.5 |
|  |  |  |


## 새로운 기능 및 향상된 기능

AEM 안내서에서는 최신 릴리스의 다양한 향상된 기능과 새로운 기능을 as a Cloud Service으로 제공합니다.

### 맵 편집기의 레이아웃 보기

이제 맵 편집기에서 DITA 맵의 전체 레이아웃을 볼 수 있습니다. 편집할 맵을 열면 **레이아웃** 맵 편집기 보기. 이 보기에서는 맵 계층을 트리 보기에서 볼 수 있고 맵에서 항목을 구성하거나 구조화할 수도 있습니다.

![레이아웃 보기](assets/layout-view-map.png)

레이아웃 보기에는 맵에 있는 주제에 대한 많은 작업을 수행하는 데 도움이 되는 별도의 도구 모음이 포함되어 있습니다.
맵에 주제 참조, 주제 그룹, 주요 정의를 삽입할 수 있습니다. 맵에 있는 주제를 위, 아래, 왼쪽 또는 오른쪽으로 이동하여 재구성할 수 있습니다. 항목을 드래그 앤 드롭하여 맵에서 이동할 수도 있습니다. 맵 편집기에서는 파일을 잠그거나 잠금 해제하고, 버전 기록을 확인하고, 버전 레이블 관리를 수행하는 아이콘도 제공합니다.


레이아웃 보기에서는 **보기 옵션** 줄 번호를 표시하거나 숨기려면 확인란을 표시하거나 숨기거나 맵에 있는 항목에 대한 파일 이름이나 제목을 표시합니다.


![보기 옵션](assets/view-options.png)

적용된 조건부 필터를 기반으로 주제를 볼 수도 있습니다.

맵 파일에서 항목을 구성하는 것 외에도 를 사용하여 참조를 추가, 이동, 복사, 붙여넣기 또는 삭제할 수도 있습니다 **옵션** 레이아웃 보기에서 요소에 사용할 수 있는 메뉴입니다. 저장소 패널에서 맵 편집기에서 연 맵으로 주제나 맵을 끌어다 놓을 수도 있습니다.

오른쪽 패널에는 맵 편집기의 레이아웃 보기에 컨텐츠 속성 및 맵 속성이 표시됩니다. 선택한 주제에 대해 정의된 인라인 속성은 레이아웃 보기의 항목에 대해 표시됩니다. 예를 들어 platform 속성이 `IOS`.

이제 주제 또는 맵에 대한 메타데이터 정보를 설정할 수도 있습니다. 선택한 주제 또는 맵에 대해 탐색 제목, 링크 텍스트, 짧은 설명 및 키워드를 정의할 수 있습니다.

![레이아웃 보기 오른쪽 패널](assets/layout-inline-attributes.png)

자세한 내용은 *레이아웃 보기* 섹션을 참조하십시오.

### 편집기 설정의 인라인 속성

이제 AEM 가이드를 사용하여 **인라인 속성** 관리자가 **편집기 설정**. 새 인라인 속성을 추가하거나 기존 속성을 **인라인 속성** 탭(편집기 설정)
주제에 대해 정의된 구성된 인라인 속성은 레이아웃 보기의 항목에 대해 표시됩니다.

![편집기 설정](assets/editor-settings-inline-attributes.png)


### 저장소 보기의 추가 필터

이제 저장소 보기의 필터 검색이 더욱 강력해졌습니다. 두 가지 새로운 검색 기준, **마지막 수정 날짜** 및 **태그** 파일을 필터링하고 AEM 저장소에서 검색 범위를 좁히기 위해 이 추가되었습니다.
* **마지막 수정 날짜**: 선택한 날짜 이후에 선택한 날짜 이전에 마지막으로 수정된 파일을 찾을 수 있습니다. 또한 사전 정의된 기준을 사용하고 지난 2시간, 지난 주, 지난 달 또는 지난 연도에 마지막으로 수정된 파일을 찾을 수 있는 옵션이 있습니다.
* **태그**: 특정 태그가 적용된 파일도 찾을 수 있습니다. 태그를 입력하거나 드롭다운 목록에서 선택할 수 있습니다.

![저장소 보기 필터](assets/repo-filter-search.png)


## 해결된 문제

다음과 같이 다양한 영역에서 해결된 버그가 있습니다.

* 사용되지 않는 Lucene 색인은 /core/article-publish/src/main/java/com/adobe/dxml/article/publish/util/DoxUtils.java (9291)에 사용됩니다.
* 업데이트된 Node.js는 게시에 사용되지 않습니다. (9835)
* DITA 항목은 **속성** 페이지. (8745)
* DITA 북맵에 추가할 때 Frontmatt 요소가 제대로 작동하지 않습니다. (9507)
* 기본 PDF | 사용 시 빈 PDF이 생성됩니다 **빠른 생성** 빈 요소를 선택한 경우 여러 파일에 사용할 수 있습니다. (9822)
* 기본 PDF | 부록 은 PDF 출력에 장으로 게시됩니다. (9829)
* 기본 PDF | SVG 이미지를 편집하면 페이지 레이아웃에 업데이트되지 않습니다. (9069)
* 일반 하이픈 문자는 `Nonbreaking Hyphen` 문자는 **특수 문자 삽입** 대화 상자. (8919)
* XML 편집기에 업데이트된 이미지가 편집된 경우 해당 항목에 표시되지 않습니다. (9500)
* 편집기를 통해 출력을 게시하는 동안 **출력** 탭. (9100)
* DITA 맵의 하위 맵은 **모두 선택** 선택 사항 을 참조하십시오. (9814)
* 맵 또는 주제 템플릿을 **템플릿** 메뉴 아래의 웹 편집기에서 사용자 지정 맵 템플릿을 선택합니다. (9846)
* 맵 또는 주제 템플릿의 하위 폴더에서 새 주제나 맵 템플릿을 만들 수 없습니다. (9888)
* 맵 또는 주제 템플릿의 하위 폴더 내에 있는 주제 또는 맵을 검색할 수 있는 옵션이 없습니다. (9889)
* Schematron 파일이 업데이트되어 DITA 파일과 함께 저장되면 오른쪽 패널이 표시되지 않습니다(DITA 파일이 Schematron 파일에 있는 유효성 검사를 차단하는 경우). (9986)
* 새 중복 출력 사전 설정은 해당 이름이 기존 사전 설정과 동일한 경우 만들 수 있습니다. (9997)
* SVG 이미지가 손상되어 HTML 출력을 생성할 때 올바르게 게시되지 않습니다. (9949)


## 알려진 문제

Adobe은 2022년 8월 AEM Guides as a Cloud Service 릴리스에 대해 다음과 같은 알려진 문제를 식별했습니다.

### 해결 방법에 대한 알려진 문제

다음과 같은 알려진 문제에 대해 주어진 해결 방법을 사용하십시오.

* 레이아웃 보기가 맵 편집기에 표시되지 않습니다.

   **해결 방법**: 폴더 프로필에서 ui_config.json을 업데이트합니다.

* Symbol.json이 무시되므로 문제가 8919가 발생합니다.

   **해결 방법**: 업데이트된 symbol.json은 재정의된 symbol.json과 병합해야 합니다.

### 기타 알려진 문제

* 저장소에서 검색을 수행한 다음 작성자 보기에서 드래그하여 놓는 데 표시된 결과 섹션에서 여러 파일을 선택하면 단일 파일만 추가됩니다.