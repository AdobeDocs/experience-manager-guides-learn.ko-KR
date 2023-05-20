---
title: 키
description: 키를 사용하면 AEM Guides에서 DITA로 작업할 때 변수 정보를 포함할 수 있습니다
exl-id: cb64e094-fe6d-4a5e-8f0e-25ae58aaa2c6
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# 키

상이한 재료들의 세트들은 선택된 장소들에서 맞춤화될 필요가 있는 유사한 정보를 포함할 수 있다. 키를 사용하면 DITA로 작업할 때 변수 정보를에 포함할 수 있습니다.

이 단원에서 사용할 수 있는 샘플 파일은 파일에 제공됩니다 [keys.zip](assets/keys.zip).

>[!VIDEO](https://video.tv.adobe.com/v/342756?quality=12&learn=on)

## 키 활성화

1. 제공된 샘플 파일 세트를 업로드합니다.

   a. zip 파일을 로드합니다.

   b. AEM 환경을 새로 고칩니다.

   c. 추출할 파일을 선택합니다.

   ![Zip 선택](images/lesson-9/select-zip.png)

   d. 클릭 [!UICONTROL **아카이브 추출**] 을 클릭합니다.

   ![도구 모음](images/lesson-9/extract-archive.png)

   e. 대화 상자에서 키라는 폴더와 같이 추출할 파일의 특정 위치를 선택합니다.

   f. 클릭 [!UICONTROL **다음**].

   g. 이전에 업로드한 적이 없는 컨텐츠에 충돌이 없으므로 모든 충돌을 건너뜁니다.

   h. 선택 [!UICONTROL **Extract**] 화면 오른쪽 상단에 있습니다.

1. 추출이 완료되면 을 클릭합니다. [!UICONTROL **대상 폴더로 이동**].

   ![확인](images/lesson-9/go-to-target.png)

## 참조된 값에 대한 키 확인

키를 올바르게 사용하려면 사용자 환경 설정에서 특정 맵을 루트 맵으로 참조해야 합니다. 이 맵 내부에는 주제 그룹 내에 함께 그룹화된 키 컬렉션이 있습니다. 맵과 항목을 열면 이 맵이 참조하는 값에 대한 키가 확인됩니다.

1. 루트 맵을 지정합니다.

   a. 키 화면에서 맵을 엽니다.

   b. 사용자 환경 설정 구성

   c. [!UICONTROL **사용자 환경 설정**] 아이콘을 클릭합니다.

   ![상단 도구 모음](images/lesson-9/author-view.png)

   d. 키 아이콘을 클릭하여 **루트 맵** 키를 확인하는 데 사용됩니다.

   e. 원하는 에셋의 확인란을 선택합니다.

   ![에셋 드롭다운](images/lesson-9/select-assets.png)

   f. 클릭 [!UICONTROL **선택**].

   g. **저장** 사용자 환경 설정.

1. 다음 위치로 이동 **맵 보기**.

1. 지정한 맵을 엽니다.

키가 해결되었습니다.

## 새 keydef 수동 추가

1. 지정된 루트 맵으로 맵을 엽니다.

1. 키를 선택합니다.

   ![키 드롭다운](images/lesson-9/hybrid-key.png)

1. 새 키 정의를 삽입합니다.

   a. 맵에서 유효한 위치를 클릭합니다.

   b. 다음을 선택합니다 **Keydef** 아이콘을 클릭합니다.

   ![Keydef 도구 모음](images/lesson-9/key-icon.png)

   c. [Keydef 삽입] 대화 상자에서 생성 중인 정의에 적합한 Keys의 고유 값을 입력합니다.

   d. 클릭 [!UICONTROL **삽입**].

1. keydef 내에 topicmeta를 추가합니다.

   a. [!UICONTROL **요소 삽입**] 아이콘을 클릭합니다.

   ![Keydef 도구 모음](images/lesson-9/add-icon.png)

   b. 요소 삽입 대화 상자에서 &quot;topicmeta&quot;를 검색하여 선택합니다.

1. topicmeta 내에 키워드를 추가합니다.

   a. [!UICONTROL **요소 삽입**] 아이콘을 클릭합니다.

   ![Keydef 도구 모음](images/lesson-9/add-icon.png)

   b. 요소 삽입 대화 상자에서 &quot;keywords&quot;를 검색하여 선택합니다.

1. topicmeta 내에 키워드를 추가합니다.

   a. [!UICONTROL **요소 삽입**] 아이콘을 클릭합니다.

   ![Keydef 도구 모음](images/lesson-9/add-icon.png)

   b. **요소 삽입** 대화 상자, 검색 및 &quot;키워드&quot; 선택

1. keydef의 값을 키워드에 입력합니다.

맵에서 keydef는 이제 다음과 같이 표시되어야 합니다.

![Keydef 완료됨](images/lesson-9/keydef.png)

## keydef를 코드 조각으로 구성

스니펫은 설명서 프로젝트의 다양한 주제에서 재사용할 수 있는 작은 콘텐츠 조각입니다. 각 keydef를 수동으로 생성하는 대신 단일 keydef를 스니펫으로 구성할 수 있습니다.

1. 맵에서 keydef 요소를 선택합니다.

1. 상황별 메뉴에서 [!UICONTROL **코드 조각 만들기**].

1. 새 코드 조각 대화 상자에서 제목 및 설명 을 추가합니다.
콘텐츠에서 기존 키 또는 키워드 정의를 제거할 수도 있습니다.

1. [!UICONTROL **만들기**]&#x200B;를 클릭합니다.

1. 왼쪽 패널에서 을 선택합니다. **코드 조각**.

1. [코드 조각] 패널에서 방금 만든 코드 조각을 맵으로 끌어서 놓습니다.

1. 콘텐츠 속성을 사용하여 필요에 따라 keydef를 업데이트합니다.
저장하고 새로 고치면 동일한 루트 맵이 포함된 맵을 정의한 모든 사용자가 이 키 세트를 사용할 수 있습니다.
