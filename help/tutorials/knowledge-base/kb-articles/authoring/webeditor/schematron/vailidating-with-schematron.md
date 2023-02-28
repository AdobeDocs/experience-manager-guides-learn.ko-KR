---
title: Webeditor의 스키마 지원
description: 웨비더에서 스키마 작업
source-git-commit: 2a036ec628424f0dedfdb69a5e860906ca100cc6
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# 웹 편집기 내에서 컨텐츠 품질 제어

이 문서에서는 AEM 안내서 웹 편집기 내의 유효성 검사 가능성에 대한 개요를 제공합니다.
디자인 웹 편집기는 시스템의 DITA 스키마 설정을 활용하여 사용자를 강제 적용하여 DITA 규격 컨텐츠를 만듭니다. 이렇게 하면 시스템에 저장된 모든 컨텐츠가 구조화되고 재사용 가능하며 유효한 DITA 컨텐츠입니다.

DITA 규칙에 대한 지원을 넘어 웹 편집기에서도 &quot;*스키마트론*&quot; 규칙을 사용합니다.

&quot;*스키마트론*&quot;은(는) XML 파일에 대한 테스트를 정의하는 데 사용되는 규칙 기반 유효성 검사 언어를 나타냅니다. 스키마 파일을 가져와 웹 편집기에서 편집할 수도 있습니다. &quot;스키마&quot; 파일을 사용하여 특정 규칙을 정의한 다음 DITA 주제 또는 맵에 대해 유효성을 검사할 수 있습니다. 스키마 규칙은 규칙으로 정의된 제한을 적용하여 XML 구조의 일관성을 보장할 수 있습니다. 이러한 제한 사항은 컨텐츠의 품질과 일관성을 보유한 SME에 의해 결정됩니다.

    참고: 웹 편집기는 ISO 스키마를 지원합니다.


## 웹 편집기에서 &quot;스키마&quot;가 작동하는 방식 알기

### 스키마 규칙 구성

의 &quot;스키마 파일 지원&quot; 섹션을 참조하십시오. [사용 안내서](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_User-Guide_EN.pdf#page=148)


### 파일 저장에 유효성 검사 규칙 적용

Webeditor 설정을 사용하면 사용자가 컨텐츠를 업데이트할 때마다 실행될 스키마 규칙/파일을 설정할 수 있습니다. 자세한 내용은 [사용 안내서](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_User-Guide_EN.pdf#page=58)

![웹 편집기 설정에서 규칙 설정](../../../assets/authoring/schematron-editorsettings-validation-tab.png)


### 수동으로 유효성 검사를 실행할 수 있습니까?

예. 컨텐츠를 작성하는 동안 작성자/사용자는 웨비더의 스키마 패널을 사용하여 스키마 파일을 업로드하고 편집기에 열려 있는 파일에서 유효성 검사를 실행할 수 있습니다.

    이를 수행하려면 폴더 프로필 관리자가 모든 사용자가 유효성 검사 패널에서 Schemtron 파일을 추가할 수 있도록 허용해야 합니다. 편집기 설정 참조(위에 표시된 스크린샷)

![스키마 파일 선택](../../../assets/authoring/schematron-rightpanel-validation-addsch.png)
![유효성 검사 실행](../../../assets/authoring/schematron-rightpanel-validation-runsch.png)


### 지원되는 규칙

현재 버전의 AEM 안내서는 &quot;검증&quot; 기반 규칙만 사용하는 유효성 검사를 지원합니다. 자세한 내용은 [자산과 보고서](https://schematron.com/document/205.html)) &quot;보고서&quot;를 기반으로 하는 모든 규칙은 아직 지원되지 않습니다.


### 스키마 규칙에 대한 샘플 및 추가 도움말

#### 샘플 사용 사례

- 링크가 외부 링크인지 및 범위가 &quot;외부&quot;인지 확인합니다

   ```
   <sch:pattern>
       <sch:rule context="xref[contains(@href, 'http') or contains(@href, 'https')]">
           <sch:assert test="@scope = 'external' and @format = 'html'">
               All external xref links must be with scope='external' and format='html'
           </sch:assert>
       </sch:rule>
   </sch:pattern>
   ```

- 맵에 &quot;topicref&quot;가 하나 이상 있는지, &quot;ul&quot; 아래에 &quot;li&quot;가 하나 이상 있는지 확인하십시오.

   ```
   <sch:pattern>
       <sch:rule context="map">
           <sch:assert test="count(topicref) > 0">
               There should be atleast one topicref in map
           </sch:assert>
       </sch:rule>
   
       <sch:rule context="ul">
           <sch:assert test="count(li) > 1" >
               A list must have more than one item.
           </sch:assert>
       </sch:rule>
   </sch:pattern>
   ```

- &quot;indexterm&quot; 요소는 항상 &quot;prolog&quot;에 있어야 합니다.

   ```
   <sch:pattern>
       <sch:rule context="*[contains(@class, ' topic/indexterm ')]">
           <sch:assert test="ancestor::node()/local-name() = 'prolog'">
               The indexterm element should be in a prolog.
           </sch:assert>
       </sch:rule>
   </sch:pattern>
   ```

#### 리소스

- 이해  [스키마 기본 사항](https://da2022.xatapult.com/#what-is-schematron)
- 추가 정보 [스키마트론의 검증 규칙](https://www.xml.com/pub/a/2003/11/12/schematron.html#Assertions)
- [샘플 스키마 파일](../../../assets/authoring/sample_schematron.sch)