---
title: 벌크 활성화 맵 컬렉션 만들기
description: 벌크 활성화 맵 컬렉션을 만드는 방법을 알아봅니다
exl-id: 7d17fb37-9486-4a3b-a421-08e279c95b6c
source-git-commit: c74badebbcb4733fb9caa79c646b1d1e5c8bfe8e
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# 벌크 활성화 맵 컬렉션 만들기 {#id214GG0E90EV}

벌크 활성화 맵 컬렉션을 만들려면 다음 단계를 수행하십시오.

1. 선택 **안내서** 을 클릭합니다.

1. 맨 위에 있는 Adobe Experience Manager 링크를 클릭하고 **도구**.

1. 을(를) 클릭합니다 **벌크 게시 대시보드** 타일.

   처음으로 빈 컬렉션 페이지가 표시됩니다. 이전에 일괄 활성화 컬렉션을 만든 경우 이 페이지에 표시됩니다.

1. **만들기**&#x200B;를 클릭합니다.

1. 벌크 활성화 맵 컬렉션의 제목을 입력하고 클릭 **만들기**.

   일괄 활성화 맵 컬렉션을 만들 때 성공 메시지가 표시됩니다.

1. 클릭 **열기** 성공 메시지 를 참조하십시오.

1. 클릭 **편집** 그런 다음 을 클릭합니다. **맵 추가**.

1. 벌크 활성화 맵 컬렉션에 추가할 DITA 맵을 찾아 추가합니다.

   기본적으로 맵과 연결된 모든 사전 설정 및 로케일이 자동으로 추가됩니다.

1. 슬라이딩 버튼을 켜거나 끔으로써 원하는 출력을 선택합니다.

   사용 가능한 로케일에서 여러 출력 사전 설정을 선택할 수 있습니다.

1. 클릭 **완료**.

   DITA 맵 파일이 벌크 활성화 맵 컬렉션에 추가됩니다.

   ![](images/bulk-activation-collection-created.png){width="800" align="left"}


맵 및 사전 설정 탭에는 다음 열에 정보가 표시됩니다.

- **맵**: DITA 맵 파일의 제목을 표시합니다.
- **맵 경로**: DITA 맵 파일의 전체 경로를 표시합니다.

- **UUID**: 파일과 연결된 고유 식별자를 표시합니다.

- **언어**: DITA 맵의 언어 코드를 표시합니다.
- **사전 설정**: 맵 파일에 구성된 출력 사전 설정 유형을 표시합니다.
- **수정됨**: DITA 맵을 마지막으로 게시한 후에 업데이트했는지 여부를 나타냅니다. 이 정보를 기반으로 이 DITA 맵에 대한 출력을 활성화할지 여부를 결정할 수 있습니다.
- **생성됨**: 마지막으로 생성된 출력의 날짜 및 시간을 표시합니다.
- **게시됨**: 마지막으로 게시된 \(또는 활성화됨\) 출력의 날짜 및 시간을 표시합니다. 링크를 클릭하면 콘텐츠가 활성화된 루트 경로에 대한 정보가 포함된 활성화 결과 페이지가 표시됩니다.


왼쪽 패널에서 사용할 수 있는 필터링 옵션은 다음과 같습니다.

- **수정됨**: 예 또는 아니오를 선택할 수 있습니다. 예를 선택하면 수정된 DITA 맵만 표시됩니다. 수정된 맵은 마지막으로 게시된 이후 생성된 맵입니다.
- **사전 설정**: 맵 파일을 필터링할 사전 설정을 선택합니다. 예를 들어 *AEM 사이트* 사전 설정을 지정하면, *AEM 사이트* 출력 사전 설정이 구성됩니다.
- **언어**: 맵 및 사전 설정 탭에서 사용 가능한 언어 코드를 선택하고 선택한 언어만 표시할 수 있습니다.

- **필터:** 최신 레일에는 다음 필터가 표시됩니다.
- **맵 및 사전 설정** 표: [맵 및 사전 설정] 테이블에는 다음 열이 표시됩니다.

**상위 항목:**[&#x200B;게시된 콘텐츠의 벌크 활성화](conf-bulk-activation.md)