---
title: 기본 PDF 게시 기능 | 기본 PDF 기능 사용자 지정 및 구성
description: 기본 PDF 기능의 다양한 구성 요소를 사용자 지정하고 구성하는 방법을 알아봅니다.
source-git-commit: bd62afd85ddbcf5f305b18b9a9c226a4790d383a
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# PDF 템플릿

템플릿을 사용하면 컨텐츠 레이아웃 및 구조의 일관성이 유지됩니다. 템플릿은 미리 정의되므로 모든 신규 프로젝트 또는 갱신에 대해 발생하는 서식 문제에 대해 재작업을 하지 않아도 됩니다. 템플릿을 사용하면 페이지 레이아웃을 디자인하고 컨텐츠를 스타일을 지정하며 다양한 설정을 적용하여 PDF을 사용자 지정할 수 있습니다.

작성자는 PDF 사전 설정을 사용하여 출력을 생성할 수 있지만 개발자는 자체 템플릿을 만들 수 있습니다. 즉시 제공되는 샘플 템플릿이 있으며 이는 개발자가 조직 요구 사항에 따라 추가로 사용자 정의하거나 복제할 수 있습니다.


## 새 PDF 템플릿 만들기 {#create-pdf-template}

특정 페이지 레이아웃으로 사용자 정의 PDF 템플릿을 만들고 스타일시트를 사용하여 페이지 레이아웃 구성 요소(예: 목차, 색인, 용어집) 또는 DITA 구성 요소(예: 제목, 단락, 목록)에 대한 서식을 정의할 수 있습니다. 처음부터 새 템플릿을 만들거나 샘플 템플릿을 사용하여 템플릿을 만들 수 있습니다.

새 PDF 템플릿을 만들려면 아래 단계를 수행하십시오.
1. 웹 편집기에서 **출력** 탭.
1. 왼쪽 사이드바를 확장하고 을(를) 클릭합니다. **템플릿**.
<img src="assets/create-pdf-template.png" alt="PDF 템플릿 만들기" width="400">
1. **템플릿** 패널에서 **템플릿** 옆에 있는 **+** 아이콘을 클릭하고 **PDF 템플릿** 선택합니다.
1. **새 템플릿** 대화 상자에서 템플릿의 이름을 지정합니다.
1. **완료** 클릭합니다.

새 템플릿이 *템플릿* 패널.

## PDF 템플릿 복제

기존 템플릿과 동일한 페이지 레이아웃과 서식을 사용하여 새 템플릿을 만들려면 복사본을 만들 수 있습니다. 템플릿이 복제되면 필요에 따라 구성 요소를 추가로 사용자 지정할 수 있습니다.

기존 PDF 템플릿을 복제하려면 아래 단계를 수행하십시오.
1. 웹 편집기에서 **출력** 탭.
1. 왼쪽 사이드바를 확장하고 을(를) 클릭합니다. **템플릿**.

   템플릿 패널이 열립니다.
1. 복제할 템플릿 위로 마우스를 가져간 다음(*옵션* 아이콘) **...** 및 **복제** 컨텍스트 메뉴에서 을 클릭합니다.

   템플릿 복제 대화 상자가 열립니다.\
   <img src="assets/duplicate-template.png" alt="중복 PDF 템플릿" width="250">
1. 팀 이름을 지정합니다.

   다음 **이름** 필드는 소스 템플릿과 동일한 이름의 사본으로 미리 채워집니다.

1. 기본 이름을 지정하려면 미리 채워진 이름을 제거하고 이름을 지정합니다.
1. 클릭 **완료**.

   템플릿 아래에 중복 템플릿이 생성되어 추가됩니다.

## PDF 템플릿 사용자 지정

템플릿 구성 요소를 수정하고 스타일시트를 사용하여 스타일 형식을 적용하여 템플릿을 사용자 지정할 수 있습니다.

PDF 템플릿을 사용자 지정하려면 아래 단계를 따르십시오.
1. 웹 편집기에서 출력 탭으로 이동합니다.
1. 왼쪽 사이드바를 확장하고 템플릿을 클릭합니다.

   템플릿 패널이 열립니다.
1. 템플릿의 구성 요소를 보려면 다음 중 하나를 수행합니다.

   * 템플릿 옆에 있는 > 아이콘을 클릭하거나 템플릿 이름을 두 번 클릭합니다.
   * 템플릿 위로 마우스를 가져간 다음 ...(옵션 아이콘)을 클릭하고, 컨텍스트 메뉴에서 편집을 선택합니다.

      기본적으로 템플릿 편집기에서 설정 패널이 열립니다.
   <img src="assets/customize-pdf-template.png" alt="PDF 팀 사용자 지정" width="350">

   사용자 지정할 수 있는 다양한 템플릿 구성 요소는 다음 섹션에 따라 분류됩니다.
   * 페이지 레이아웃: 일반적인 PDF에는 전면 표지 또는 제목 페이지, TOC, 장, 색인 등의 다양한 페이지가 포함되어 있습니다. PDF 레이아웃 섹션을 사용하면 페이지를 구성하는 다양한 페이지의 모양과 느낌을 디자인할 수 있습니다. 모양새 이외에 페이지의 머리글, 바닥글 및 콘텐츠 영역과 같은 페이지 요소의 배열을 정의할 수도 있습니다. 페이지 레이아웃 사용자 지정에 대한 자세한 내용은 ***페이지 레이아웃 만들기 및 사용자 지정***.
   * 스타일 시트: 스타일 시트 섹션의 설정을 사용하면 TOC, 색인, 용어집 등과 같은 페이지 레이아웃 구성 요소의 모양과 느낌을 사용자 지정할 수 있습니다. 또한 제목, 단락, 목록 등과 같은 DITA 컨텐츠의 스타일을 사용자 정의할 수도 있습니다. 스타일시트 사용에 대한 자세한 내용은 ***스타일시트를 사용하여 PDF 사용자 정의***.
   * 리소스: PDF 템플릿을 사용자 지정하거나 디자인하는 데 필요한 자산 파일을 저장합니다. 로고, 사용자 정의 글꼴, 배경 이미지 등의 자산은 리소스에 저장됩니다. 리소스 사용에 대한 자세한 내용은 ***리소스를 사용한 작업***.
   * 설정: 템플릿을 사용하여 PDF 생성을 위한 출력 설정을 구성합니다. 이 섹션에서는 PDF, 장 시작 페이지, 인쇄 마커 등의 여러 페이지에 대한 템플릿 매핑을 정의할 수 있습니다. 설정 적용에 대한 자세한 내용은 ***고급 PDF 설정***.
1. 템플릿 구성 요소를 사용자 지정하려면 템플릿 구성 요소를 두 번 클릭하거나 앞에 > 아이콘을 클릭하십시오.

   예를 들어 *페이지 레이아웃* 또는 *>* 앞에 아이콘 표시 *페이지 레이아웃* 사용 가능한 페이지 레이아웃을 보려면
1. 원하는 대로 변경한 후 *모두 저장* 또는 `Ctrl+S`).

