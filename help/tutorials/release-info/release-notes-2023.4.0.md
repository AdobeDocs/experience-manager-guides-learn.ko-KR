---
title: 릴리스 노트 | Adobe Experience Manager 안내서 as a Cloud Service, 2023년 4월 릴리스
description: Adobe Experience Manager 안내서의 최신 릴리스 as a Cloud Service
exl-id: 3b09f0b3-cfa4-422d-91b7-733ab1c1896c
source-git-commit: cf612da41f79b0bf9da4c4d7454a0e3c86af7a4c
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 2%

---

# Adobe Experience Manager 안내서 4월 릴리스 as a Cloud Service

## 최신 릴리스로 업그레이드

현재 Adobe Experience Manager 가이드를 as a Cloud Service(라고 함)로 업그레이드합니다 *AEM 안내서 as a Cloud Service*) 다음 단계를 수행하여 설정합니다.

1. Cloud Services의 Git 코드를 확인하고 업그레이드하려는 환경에 해당하는 Cloud Services 파이프라인에 구성된 분기로 전환합니다.
2. 업데이트 `<dox.version>` 속성 `/dox/dox.installer/pom.xml` Cloud Services Git 코드 파일을 2023.4.249에 추가합니다.
3. 변경 사항을 커밋하고 Cloud Services 파이프라인을 실행하여 AEM Guides as a Cloud Service 최신 릴리스로 업그레이드합니다.

## 기존 컨텐츠를 색인화하는 단계(AEM 안내서 9월 릴리스 이전 버전을 사용 중인 경우에만 as a Cloud Service)

기존 컨텐츠를 인덱싱하고 맵 수준에서 새 찾기 및 바꾸기 텍스트를 사용하는 다음 단계를 수행합니다.

* 서버에 대한 POST 요청 실행(올바른 인증 사용) - `http://<server:port>/bin/guides/map-find/indexing`.
(선택 사항: 맵의 특정 경로를 전달하여 색인화할 수 있습니다. 기본적으로 모든 맵은 색인화됩니다 || 예 : `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* API가 jobId를 반환합니다. 작업 상태를 확인하려면 작업 ID가 있는 GET 요청을 동일한 종료 지점으로 보낼 수 있습니다. `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(예: http://&lt;
_localhost:8080_>/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 작업이 완료되면 위의 GET 요청이 성공에 응답하고 맵이 실패한 경우 이에 대해 설명합니다. 성공적으로 인덱싱된 맵은 서버 로그에서 확인할 수 있습니다.

## 호환성 매트릭스

이 섹션에는 AEM Guides as a Cloud Service 2023년 4월 릴리스에서 지원하는 소프트웨어 응용 프로그램의 호환성 매트릭스가 나와 있습니다.

### FrameMaker 및 FrameMaker Publishing Server

| AEM Guides as a Cloud Release | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.04.0 | 호환되지 않음 | 2022년 이상 |
|  |  |  |


### 산소 커넥터

| AEM Guides as a Cloud Release | 산소 커넥터 창 | 산소 커넥터 Mac | 산소 창에서 편집 | Oxygen Mac에서 편집 |
| --- | --- | --- | --- | --- |
| 2023.04.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


## 새로운 기능 및 향상된 기능

AEM 안내서에서는 최신 릴리스의 향상된 기능과 새로운 기능을 제공합니다.

### PDF 게시에서 고급 메타데이터 지원

이제 AEM 안내서에서는 PDF 출력의 메타데이터에 매핑된 메타데이터에 대한 고급 지원을 제공합니다. 메타데이터 옵션에는 작성자 이름, 문서 제목, 키워드, 저작권 정보 및 기타 데이터 필드와 같은 문서 및 해당 컨텐츠에 대한 정보가 포함됩니다.

<img src="assets/pdf-metadata.png" alt=" 기본 pdf 메타데이터">

XMP 파일을 가져올 수 있고 AEM 가이드가 파일에서 정보를 선택할 수 있습니다. 드롭다운을 사용하여 메타데이터 이름 및 값을 제공하는 선택 사항도 있습니다. 이름 필드에 직접 입력하여 사용자 지정 메타데이터를 추가할 수도 있습니다.


### 향상된 개요 보기 패널

AEM Guides는 문서에 사용되는 요소의 계층 보기를 가져올 수 있는 향상된 개요 보기 패널을 제공합니다.

<img src="assets/select-element-content-outline-view_cs.png" alt=" 기본 pdf 메타데이터">

아웃라인 보기는 다음과 같은 개선 사항을 제공합니다.

* 개요 보기 옵션 드롭다운이 개요 보기 패널 맨 위에 표시됩니다. 요소에 ID, 속성 및 텍스트가 있는 경우 드롭다운에서 선택하여 요소와 함께 표시할 수 있습니다. 아웃라인 뷰 패널에 표시할 수 있는 속성은 관리자가 내에서 구성한 디스플레이 속성 설정에 의해 결정됩니다 **편집기 설정**.

* 검색 기능을 사용하여 이름, ID, 텍스트 또는 속성 값으로 요소를 검색할 수 있습니다.


### AEM 안내서 as a Cloud Service용 마이크로서비스 기반 게시

AEM Guides는 마이크로 서비스 기반 게시와 동시에 대규모 게시 작업 로드를 실행하고 업계 선도적인 Adobe I/O Runtime 서버를 사용하지 않는 플랫폼을 활용하는 기능을 as a Cloud Service으로 제공합니다.

4월 릴리스에서는 여러 게시 요청을 동시에 실행하고 마이크로 서비스 기반 기본 PDF 게시를 사용하여 대량 PDF 출력을 매우 효율적으로 생성할 수 있습니다.
자세한 내용은 [AEM 안내서 as a Cloud Service에 대한 새로운 마이크로서비스 기반 게시 구성](../knowledge-base/publishing/configure-microservices.md).


## 해결된 문제

다음과 같이 다양한 영역에서 해결된 버그가 있습니다.

* 기본 PDF | Brackets()가 있는 출력 클래스가 있는 컨텐츠를 게시하면 게시가 중지됩니다. (11596)
* 변경 내용 추적이 켜진 기존 목록 항목 대신 이동(드래그 앤 드롭)할 때 문제가 발생합니다. (11570)
* 변경 내용 추적이 켜진 새 목록 항목으로 이동(드래그 앤 드롭)할 때 문제가 발생합니다. (11569)
* Track Changes on에서 들여쓰기 또는 내어쓰기 목록 항목이 예상대로 작동하지 않습니다. (11568)
* 변경 내용 추적 이 켜져 있는 행에 컨텐츠를 추가한 다음 변경 내용 추적 을 끄면 실제로 해당 컨텐츠가 해제되지 않습니다. (11567)
* 목록 항목을 드래그 앤 드롭하는 데 어려움이 있으면 목록 항목 대신 텍스트가 이동됩니다. (11566)
* 완료된 검토가 읽기 전용 모드로 열리지 않습니다. (11387)
* AEM 사이트 검색에서 문제가 발생합니다(2-3 수준 노드 이후에는 작동하지 않습니다.). (11352)
* 녹색(변경 사항 추적)으로 표시된 요소에서 작성 시 추적 변경이 비활성화되어 있더라도 새 컨텐츠는 추적 변경 사항으로 표시됩니다. (7021)

### 해결 방법에 대해 알려진 문제

Adobe은 2023년 4월 AEM Guides as a Cloud Service 릴리스에 대해 알려진 다음과 같은 문제를 식별했습니다.

* 기본 PDF | 이전 메타데이터는 출력 사전 설정이 명시적으로 열릴 때까지 채워지지 않습니다.
