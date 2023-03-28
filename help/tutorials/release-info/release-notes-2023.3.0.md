---
title: 릴리스 노트 | Adobe Experience Manager 안내서 as a Cloud Service, 2023년 3월 릴리스
description: Adobe Experience Manager 안내서의 최신 릴리스 as a Cloud Service
source-git-commit: 27c8c0f3ac5c6d9c318ac8fb7ed13299ac9994de
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 2%

---

# Adobe Experience Manager 안내서 3월 릴리스 as a Cloud Service

## 최신 릴리스로 업그레이드

현재 Adobe Experience Manager 가이드를 as a Cloud Service(라고 함)로 업그레이드합니다 *AEM 안내서 as a Cloud Service*) 다음 단계를 수행하여 설정합니다.
1. Cloud Services의 Git 코드를 확인하고 업그레이드하려는 환경에 해당하는 Cloud Services 파이프라인에 구성된 분기로 전환합니다.
2. 업데이트 `<dox.version>` 속성 `/dox/dox.installer/pom.xml` Cloud Services Git 코드 파일을 2023.3.242에 추가합니다.
3. 변경 사항을 커밋하고 Cloud Services 파이프라인을 실행하여 AEM Guides as a Cloud Service 최신 릴리스로 업그레이드합니다.

## 기존 컨텐츠를 색인화하는 단계(AEM 안내서 9월 릴리스 이전 버전을 사용 중인 경우에만 as a Cloud Service)

기존 컨텐츠를 인덱싱하고 맵 수준에서 새 찾기 및 바꾸기 텍스트를 사용하려면 다음 단계를 수행하십시오.

* 서버에 대한 POST 요청 실행(올바른 인증 사용) - `http://<server:port>/bin/guides/map-find/indexing`.
(선택 사항: 맵의 특정 경로를 전달하여 색인화할 수 있습니다. 기본적으로 모든 맵은 색인화됩니다 || 예 : `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* API가 jobId를 반환합니다. 작업 상태를 확인하려면 작업 ID가 있는 GET 요청을 동일한 종료 지점으로 보낼 수 있습니다. `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(예: http://&lt;
_localhost:8080_>/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 작업이 완료되면 위의 GET 요청이 성공에 응답하고 맵이 실패한 경우 이에 대해 설명합니다. 성공적으로 인덱싱된 맵은 서버 로그에서 확인할 수 있습니다.

## 호환성 매트릭스

이 섹션에는 AEM Guides as a Cloud Service 2023년 3월 릴리스에서 지원하는 소프트웨어 응용 프로그램의 호환성 매트릭스가 나와 있습니다.

### FrameMaker 및 FrameMaker Publishing Server

| AEM Guides as a Cloud Release | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.03.0 | 호환되지 않음 | 2022년 이상 |
|  |  |  |


### 산소 커넥터

| AEM Guides as a Cloud Release | 산소 커넥터 창 | 산소 커넥터 Mac | 산소 창에서 편집 | Oxygen Mac에서 편집 |
| --- | --- | --- | --- | --- |
| 2023.03.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


## 새로운 기능 및 향상된 기능

AEM 안내서에서는 최신 릴리스의 향상된 기능과 새로운 기능을 제공합니다.

### 웹 편집기에서 비디오 또는 오디오 파일 열기 및 재생

이제 AEM 안내서에서는 웹 편집기에서 오디오 또는 비디오 파일을 열고 재생하는 기능을 제공합니다. 볼륨 또는 비디오 보기를 변경할 수 있습니다. 바로 가기 메뉴에는 다음과 같은 옵션이 있습니다 **다운로드**, 변경 **재생 속도**, 또는 보기 **화면 속 화면**.

<img src="assets/video-web-editor.png" alt="비디오 재생" width="600">


## 해결된 문제

다음과 같이 다양한 영역에서 해결된 버그가 있습니다.

* 다운로드 PDF 프로세스가 웹 편집기에서 제대로 작동하지 않습니다. (11496)
* JSON 출력 | 속성 값을 로 갖는 메타데이터 매핑 `"value in spaces and double quotes"` 이로 인해 게시 오류가 발생합니다. (11438)
* 오디오 및 비디오 멀티미디어 파일을 삽입할 때 **멀티미디어 삽입** 아이콘. (11320)
* 전문 제목 요소가 있는 템플릿을 사용하여 맵을 만들 때 유효성 검사 오류가 발생합니다. (11212)
* 기본 PDF | 표 머리글에 있는 각주는 PDF 출력 내의 해당 페이지 바닥글에 굵게 맞춤되고 가운데 맞춤된 텍스트를 표시합니다. (10610)
>[!NOTE]
>
>기본 PDF 변경 사항을 반영하려면 /content/dam/dita-templates에 있는 PDF 폴더를 삭제한 다음 최신 빌드로 업그레이드하십시오. (10610)

### 해결 방법에 대해 알려진 문제

Adobe은 2023년 3월 AEM Guides as a Cloud Service 릴리스에 대해 알려진 다음과 같은 문제를 확인했습니다.

* 사용자는 중복된 자산의 버전을 저장하거나 만들 수 없습니다.

**해결 방법**: 중복 자산을 변경하기 전에 자산 UI에서 다시 처리합니다.

