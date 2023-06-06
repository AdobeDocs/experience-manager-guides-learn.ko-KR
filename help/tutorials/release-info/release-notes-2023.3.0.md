---
title: 릴리스 정보 | Adobe Experience Manager Guides as a Cloud Service, 2023년 3월 릴리스
description: Adobe Experience Manager Guides as a Cloud Service 3월 릴리스
source-git-commit: 99ca14a816630f5f0ec1dc72ba77994ffa71dff6
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 1%

---


# 2023년 3월 Adobe Experience Manager 가이드 as a Cloud Service 릴리스

이 릴리스 노트는 2023년 3월 Adobe Experience Manager Guides(이후 설명됨)의 버전에서 해결된 업그레이드 지침, 호환성 매트릭스 및 문제를 다룹니다. *AEM Guides as a Cloud Service*).

새로운 기능 및 향상된 기능에 대한 자세한 내용은 [AEM Guides as a Cloud Service의 2023년 3월 릴리스의 새로운 기능](whats-new-2023.3.0.md).

## 2023년 3월 릴리스로 업그레이드

다음 단계를 수행하여 현재 AEM Guides as a Cloud Service 설정을 업그레이드하십시오.
1. Cloud Services의 Git 코드를 체크아웃하고 업그레이드하려는 환경에 해당하는 Cloud Services 파이프라인에 구성된 분기로 전환합니다.
2. 업데이트 `<dox.version>` 의 속성 `/dox/dox.installer/pom.xml` Cloud Services 파일 Git 코드 2023.3.242로.
3. 변경 사항을 커밋하고 Cloud Services 파이프라인을 실행하여 AEM Guides as a Cloud Service의 2023년 3월 릴리스로 업그레이드합니다.

## 기존 콘텐츠를 색인화하는 절차(AEM Guides의 9월 릴리스 이전 버전을 as a Cloud Service으로 사용하는 경우에만)

기존 콘텐츠를 색인화하고 맵 수준에서 새 찾기 및 바꾸기 텍스트를 사용하려면 다음 단계를 수행하십시오.

* 올바른 인증을 사용하여 서버에 대한 POST 요청 실행 - `http://<server:port>/bin/guides/map-find/indexing`.
(선택 사항: 맵의 특정 경로를 전달하여 인덱싱할 수 있습니다. 기본적으로 모든 맵이 인덱싱됩니다 || 예 : `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* API는 jobId를 반환합니다. 작업 상태를 확인하려면 작업 ID가 있는 GET 요청을 동일한 끝점으로 보낼 수 있습니다. `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(예: http://&lt;
_localhost:8080_>/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 작업이 완료되면 위의 GET 요청은 성공으로 응답하고 맵이 실패한 경우 언급됩니다. 인덱싱된 맵은 서버 로그에서 확인할 수 있습니다.

## 호환성 매트릭스

이 섹션에서는 2023년 3월 AEM Guides as a Cloud Service 릴리스에서 지원되는 소프트웨어 애플리케이션에 대한 호환성 매트릭스를 나열합니다.

### FrameMaker 및 FrameMaker Publishing Server

| AEM Guides as a Cloud 릴리스 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.03.0 | 호환되지 않음 | 2022년 이상 |
|  |  |  |


### 산소 연결기

| AEM Guides as a Cloud 릴리스 | 산소 커넥터 창 | 산소 커넥터 Mac | Oxygen 창에서 편집 | Oxygen Mac에서 편집 |
| --- | --- | --- | --- | --- |
| 2023.03.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


