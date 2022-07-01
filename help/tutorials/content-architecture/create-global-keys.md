---
title: 글로벌 키 만들기
description: 조직 컨텐츠에서 사용할 글로벌 키를 만드는 방법
role: Admin
exl-id: b8e3a6d2-ea82-4fdb-bd16-3f4b6594af52
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# 글로벌 키 만들기

조직은 제품 이름이나 제품 피치와 같이 여러 위치에서 사용되지만 쉽게 변경할 수 있는 유연하고 일반적인 텍스트가 있는 경우 키를 사용해야 합니다. 이러한 재사용 가능한 텍스트에 대한 키를 사용하면 키 값과 같이 한 위치에서 변경 작업을 수행하여 여러 위치에서 업데이트를 푸시할 수 있습니다.

## 1단계: 키 저장을 위한 글로벌 맵 만들기

맵 만들기 및 추가 [!UICONTROL keyref] 요소를 추가합니다.

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "technicalContent/dtd/map.dtd">
<mapid="map.ditamap_ffbdbf06-8658-4311-ad84-1c631bba904f">
  <title>global-keys-map</title>
  <keydefkeys="adobe">
    <topicmeta>
      <linktext>Adobe Systems</linktext>
    </topicmeta>
  </keydef>
  <keydefkeys="AEM">
    <topicmeta>
      <linktext>Adobe Experience Manager</linktext>
    </topicmeta>
  </keydef>
</map>
```

여기에서 위에 표시된 대로 두 개의 정의를 정의했으며, [!UICONTROL keyref] 로서의 _AEM_ 대상 _Adobe Experience Manager_ 텍스트.

## 2단계: 이 맵을 게시 맵에 추가합니다

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "technicalContent/dtd/map.dtd">
<mapid="map.ditamap_cbf4a96d-e382-4e8c-8830-bcc093fe6638">
  <title>sample-map</title>
  <topicrefhref="sample-topic-using-the-keys.dita"type="topic">
  </topicref>
  <maprefformat="ditamap"href="global-keys-map.ditamap"type="map">
  </mapref>
</map>
```

## 3단계: 키를 사용하여 글로벌 키 맵에 정의된 변수를 참조합니다

+ 항목을 편집하고 키 값을 [!UICONTROL keyref].
+ 스크린샷에 표시된 것처럼 키워드를 선택할 수 있는 작은 창이 나타납니다. &quot;키워드&quot; 요소를 추가하면 표시됩니다.
   ![요소 삽입](assets/insert_element.png)
   ![키 참조](assets/key_ref.png)

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE topic PUBLIC "-//OASIS//DTD DITA Topic//EN" "technicalContent/dtd/topic.dtd">
<topicid="topic.dita_31b00e61-04b5-4193-af7a-68503e88b087">
  <title>sample-topic-using-the-keys</title>
  <shortdesc></shortdesc>
  <body>
    <p>This is a sample topic using the keys defined in the global map</p>
    <p>here i am using the key definition for AEM :<keywordkeyref="AEM"></keyword></p>
  </body>
</topic>
```
