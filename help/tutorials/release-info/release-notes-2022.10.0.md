---
title: 릴리스 노트 | Adobe Experience Manager 안내서 as a Cloud Service, 2022년 10월 릴리스
description: Adobe Experience Manager 안내서 10월 릴리스 as a Cloud Service
exl-id: 38638080-625c-49c3-9e54-56cc23831546
source-git-commit: 4183162142f5f6291fdb6e832e10b46a3c0da73a
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 4%

---

# Adobe Experience Manager 안내서 10월 릴리스 as a Cloud Service

## 10월 릴리스로 업그레이드

현재 Adobe Experience Manager 가이드를 as a Cloud Service(라고 함)로 업그레이드합니다 *AEM 안내서 as a Cloud Service*) 다음 단계를 수행하여 설정합니다.
1. Cloud Services의 Git 코드를 확인하고 업그레이드하려는 환경에 해당하는 Cloud Services 파이프라인에 구성된 분기로 전환합니다.
2. 업데이트 `<dox.version>` 속성 `/dox/dox.installer/pom.xml` Cloud Services Git 코드 파일에 2022.10.183.
3. 변경 사항을 커밋하고 Cloud Services 파이프라인을 실행하여 AEM Guides as a Cloud Service 10월 릴리스로 업그레이드합니다.

## 호환성 매트릭스

이 섹션에는 AEM Guides as a Cloud Service 2022년 10월 릴리스에서 지원하는 소프트웨어 응용 프로그램의 호환성 매트릭스가 나와 있습니다.

### FrameMaker 및 FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 호환되지 않음 | 2020 업데이트 4 이상 |
|  |  |

*AEM에서 작성된 기준 및 조건은 2020.2년부터 MPS 릴리스에서 지원됩니다.

### 산소 커넥터

| AEM Guides as a Cloud Release | 산소 커넥터 창 | 산소 커넥터 Mac | 산소 창에서 편집 | Oxygen Mac에서 편집 |
| --- | --- | --- | --- | --- |
| 2022.10.0 | 2.7.13 | 2.7.13 | 2.3 | 2.3 |
|  |  |  |  |


## 새로운 기능 및 향상된 기능

AEM 안내서에서는 as a Cloud Service으로 10월 릴리스의 향상된 기능과 새로운 기능을 제공합니다.


### 빠른 생성 패널

이제 AEM 안내서에서는 **빠른 생성** DITA 맵용으로 만든 사전 설정의 출력을 빠르게 생성하고 보는 데 도움이 되는 패널입니다.

![빠른 생성 아이콘](assets/quick-generate-icon.png)

에서 **빠른 생성** 패널에서는 DITA 맵용으로 만든 모든 출력 사전 설정 목록을 볼 수 있습니다.

![빠른 생성 패널](assets/quick-generate-panel.png)

하나 이상의 사전 설정을 선택하고 출력을 빠르게 생성합니다. 사전 설정에 대해 생성된 출력을 빠르게 볼 수도 있습니다. 출력 생성에 성공 메시지가 표시됩니다. 출력 생성에 실패하면 오류 메시지가 표시됩니다. 오류 로그를 확인하여 생성 프로세스에서 발생한 오류의 세부 정보를 확인할 수도 있습니다.


## 해결된 문제

다음과 같이 다양한 영역에서 해결된 버그가 있습니다.

* 기본 PDF | PDF 출력에서 리소스 전용 항목을 제거할 때 오류가 발생합니다. (10554)
* 기본 PDF | 빈 Keyrefs가 PDF 출력에 나타납니다. (10553)
* 기본 PDF | `navtitle` 대상 `topichead` 가 영광이 아닙니다. (10509)
* 기본 PDF | amd64 JDK 향수에 필요한 지원. (10465)
* 기본 PDF | 목차 항목을 숨길 수 없습니다. (10355)
* 기본 PDF | 장 레이아웃에서 페이지 번호를 다시 시작하면 이전 장의 끝에서 번호 매기기를 임의로 시작합니다. (10154)
* Chrome 브라우저 | UI에서 요소를 드래그하여 놓을 때 화면이 비어 있게 됩니다. 예를 들어 조건 패널에서 조건을 드래그할 때 (10524)
* 자산의 복사-붙여넣기 작업 후 노드 속성이 제거됩니다. (10053)
* 클릭 시  **닫기** 사용자가 assets로 리디렉션되었습니다. 사용자를 AEM 홈페이지로 유도하기 위해 경험이 수정되었습니다. (9654)
