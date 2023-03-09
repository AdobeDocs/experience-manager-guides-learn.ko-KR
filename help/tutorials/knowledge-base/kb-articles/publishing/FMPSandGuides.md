---
title: FMPS 및 AEM 안내서
description: AEM Guides를 사용하여 FMPS로 게시
source-git-commit: abf6b9502615e5029ce51f860e05cadc8d94edc2
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---



# FrameMaker Publishing Server(FMPS) 및 AEM 안내서

**고품질의 자동화된 게시를 원하는 경우 FrameMaker Publishing Server와 AEM Guides를 통합하면 솔루션을 구축할 수 있습니다.\
아래 문서는 AEM Guides를 사용하여 FMPS를 설정하고 실행하는 데 도움이 됩니다.**

## AEM Guides와 FMPS의 호환성:

- 4.1 AEM Guides 와의 호환성: [링크](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/release-notes/on-prem-release-notes/release-notes-4.1.html?lang=en/#compatibility-matrix)

- 4.0 AEM Guides 와의 호환성: [링크](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-4-0.html/#Compatibility%20matrix)

- 향후 릴리스: [링크](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/latest-release-info.html?lang=en)

## 설치:

### AEM 안내서:

설치 및 구성은 를 참조하십시오. [링크](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-1-2/Adobe-Experience-Manager-Guides_Installation-Configuration-Guide_EN.pdf)

### FMPS:

FMPS 설치의 경우 다음을 참조할 수 있습니다 [비디오 링크](https://www.youtube.com/watch?v=2deelyM5VA8&amp;t) 또는 [설명서](https://help.adobe.com/en_US/framemaker/server/index.html#t=fmps-user-guide%2Finstall_config_fmps.html%23install_config_fmps&amp;rhtocid=_2)

## 필수 구성 :

DITA 컨텐트는 FMPS(FrameMaker Publishing Server)를 사용하여 출력할 수 있습니다. FMPS가 지원하는 다양한 형식으로 출력을 만들 수 있습니다.
웹 콘솔에서 com.adobe.fmdita.config.ConfigManager 번들의 다음 속성을 수정하여 FMPS를 사용하도록 AEM Guides를 설정합니다.

웹 콘솔을 열려면 URL 액세스 http:// 로 이동합니다.&lt;server name=&quot;&quot;>:\&lt;port>/system/console/configMgr .

**구성 속성 및 설명:** [링크](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-1-2/Adobe-Experience-Manager-Guides_Installation-Configuration-Guide_EN.pdf#page=89)

## 테스트 실행:

FMPS를 사용하면 자동으로 게시할 수 있습니다 **PDF, 반응형 HTML5**, 및 **Epub** DITA 및 FM 에셋용

&quot;다음을 사용하여 PDF 생성&quot; 메뉴에서 FrameMaker Publishing Server를 선택합니다.

사용자는 &quot;Settings File(.sts)&quot; 및 &quot;ditaval&quot;을 제공할 수 있습니다. 필터링은 제공한 조건에 따라 Ditaval을 사용하여 수행됩니다.

- **파일 설정 중**: FrameMaker /FMPS 게시 설정으로서, 게시 중에 FMPS에서 적용할 모든 설정이 들어 있습니다. 예: ,사용자 지정된 템플릿으로 출력 생성 , 표시 및 재단 물림(PDF) 생성 , TOC로 PDF 생성 , 색인 등.
- **FMP 표시:** Ditaval 및 설정 파일 의 사전 정의된 조합 을 사용하면 별도의 Ditaval 및 설정 파일 을 제공하는 대신 게시 요구에 다시 사용할 수 있는 FMPS 사전 설정을 미리 만들 수 있습니다.

**참고:**  설정 또는 FMPS 사전 설정을 선택하지 않으면 FMPS가 기본 시스템 설정으로 게시됩니다.

FMPS 사전 설정을 선택하고 AEM에서 설정/Ditaval 파일도 제공한 경우 충돌하고 FMPS 사전 설정이 사용자 지정 설정/Ditaval 파일보다 우선합니다.

### FMPS를 사용한 기준선 게시:

FMPS2020.0.2 이상 버전으로 이미 생성된 기준선을 게시할 수 있습니다.

**시작할 샘플 FMPS 설정 파일(.sts 파일):** [링크](https://acrobat.adobe.com/link/track?uri=urn:aaid:scds:US:ef750752-7a7e-4e51-923e-6b7d9861ed54) (이 파일의 압축 풀기)

## FAQ 및 문제 해결:

- ### FMPS 게시가 &quot;시간 초과 예외&quot;로 실패합니다.

/system/console/configMgr/com.adobe.fmdita.config.ConfigManager&quot;에서 &quot;FMPS 시간 초과&quot;(초) 값을 확인하고 늘립니다.

- ### 드롭다운에서 FMPS 사전 설정을 가져올 수 없음

서버에 미리 정의된 FMPS 사전 설정이 만들어져 있고 연결 설정이 올바른지 확인하십시오.

- ### 게시할 때 빈 PDF이 표시됩니다.

UUID를 사용하는 경우 FrameMaker EditPreferences에서 &quot;UUID 기반 참조 사용&quot;을 선택했는지 확인하고 비 UUID AEM guides에 대해 그 반대의 경우도 확인하십시오

- ### 내 설정/Ditaval이 최종 게시된 출력에 적용되지 않습니다.

Setting/Ditaval 파일과 FMPS 사전 설정을 모두 병렬로 선택하지 않았는지 확인합니다.FrameMaker를 사용하여 출력을 수동으로 확인합니다.

- ### 기준선이 FMPS에서 게시되지 않음

기준선 게시는 FMPS2020.0.2 이상 버전과 호환됩니다.\
기준선이 제대로 생성되었는지 확인하려면 대시보드 항목 다운로드 맵 매핑으로 이동하여 &quot;기준선 사용&quot;을 선택합니다.

- ### FMPS에서 작업을 게시하는 데 다른 엔진보다 시간이 더 걸립니다.

approx의 이상적인 고정 헤더가 있을 것입니다. 다른 엔진 이외의 FMPS에서 게시하는 동안에만 3~4분이 소요되며 그 이상이라고 생각되는 경우 FMPS 관리자에게 문의하거나 Adobe 지원 센터에 문의하십시오.

## 기타 리소스:

[FMPS 학습 및 지원](https://helpx.adobe.com/support/framemaker-publishing-server.html)

[AEM 학습 및 지원](https://helpx.adobe.com/in/support/xml-documentation-for-experience-manager.html)

[FrameMaker 및 FMPS 커뮤니티](https://community.adobe.com/t5/framemaker/ct-p/ct-framemaker?page=1&amp;sort=latest_replies&amp;lang=all&amp;tabid=all)

[AEM Guides 커뮤니티](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation)
