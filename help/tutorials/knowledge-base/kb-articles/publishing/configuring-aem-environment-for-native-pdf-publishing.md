---
title: 기본 PDF 게시를 위한 AEM 환경 구성
description: 기본 PDF 게시를 위한 AEM 환경 구성
source-git-commit: f26b8f94e1d7a3c9dd0aaab2eb196a77119e47ac
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 1%

---


# 기본 PDF 게시를 위한 AEM 환경 구성

AEM 안내서에는 사용자가 컨텐츠를 PDF 형식으로 디자인, 개발 및 게시할 수 있도록 하는 기본 PDF 게시 엔진이 포함되어 있습니다.

페이지 레이아웃 및 CSS와 함께 다양한 페이지 레이아웃, CSS 템플릿을 만들고 PDF 템플릿을 디자인하는 기능을 제공합니다.

AEM 안내서에서 이 기본 PDF을 구성하는 단계는 운영 체제에 따라 다릅니다. AEM이 설치된 운영 체제에 따라 아래 구성 단계를 사용하십시오.

## 사전 요구 사항

기본 PDF 설정을 위한 최소 요구 사항:

- 설치된 Java Platform, Standard Edition 8 또는 11 JDK(Java SE Development Kit) 및 JRE(Java SE Runtime Environment)
- AEM 6.5 SP13, SP12, SP11 또는 SP10
- 안내서 4.1 이상 버전(비UUID 또는 UUID)

기본 PDF 게시 엔진에서는 AEM crx-quickstart 폴더에서 노드 모듈을 생성하려면 Oracle JDK가 필요합니다. 기본적으로 다음 운영 체제를 지원합니다.

- Windows 10, windows 2019 server 이상
- Linux - (RHEL 8 이상, CentOS 7 이상, Ubuntu 18 이상 버전)
- Mac OS(Intel 기반)

## Windows Server용 구성 단계(JAVA 11/8)

1. AEM 서버가 다운되었는지 확인합니다.
2. Windows 작업 표시줄에서 Windows 아이콘을 마우스 오른쪽 단추로 클릭하고 시스템을 선택합니다.
3. 설정 창의 관련 설정에서 고급 시스템 설정을 클릭합니다.
4. 고급 탭에서 환경 변수를 클릭합니다.
5. 시스템 변수 섹션에서 &quot;_새로 만들기_&quot; 새 환경 변수를 만들려면
6. 변수 이름을 JAVA_HOME으로 입력합니다.
7. 값 필드에서 Java 설치 경로를 입력하고 확인을 클릭합니다.

   예:

   JAVA 11:

   C:\Program Files\JAVA\jdk-11.0.15.1

   JAVA 8:

   C:\Program Files\JAVA\ jdk1.8.0_144

8. 시스템 변수에서 경로 를 추가하고 편집을 클릭합니다.

9. 이제 Path 변수 내에서 서버 경로 값을 제공하고 확인을 클릭합니다.

   예:

   JAVA 11:

   %JAVA_HOME%\bin\server\

   JAVA 8:

   %JAVA_HOME%\jre\bin\server\

10. 환경 변수 대화 상자에서 &#39;확인&#39;을 다시 클릭합니다.
11. 시스템 속성 대화 상자에서 &#39;확인&#39;을 다시 클릭합니다.
12. 이제 AEM 서버를 시작합니다.
13. 웹 편집기에서 사전 설정에서 기본 PDF을 생성합니다.

## Linux Server용 구성 단계(RHEL7/centOS 7)

1. AEM 서버가 다운되었는지 확인합니다.
2. $JAVA_HOME을 에코 하여 JAVA_HOME 변수를 확인합니다.
3. JAVA_HOME 변수가 설정되지 않은 경우 4단계를 수행합니다. 그렇지 않으면 5단계로 직접 이동합니다.
4. 설치된 Java 버전을 기준으로 아래 명령을 사용하여 JAVA_HOME 변수를 설정합니다.

   예:

   JAVA 11:

   1. export JAVA\_HOME=/usr/lib/jvm/java-11.0.15.1
   2. 내보내기 경로=$경로: $JAVA\_HOME/bin
   3. export LD\_LIBRARY\_PATH=/usr/lib/jvm/jdk-11.0.15.1/lib/server:/usr/java/jdk-11.0.15.1/lib/server

   JAVA 8:

   1. export JAVA\_HOME=/usr/lib/jvm/java-11.0.15.1
   2. 내보내기 경로=$경로: $JAVA\_HOME/bin


5. AEM Server 다시 시작
6. &quot;_node_modules.zip_&quot; 이 문서의 하단에 crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166/ 디렉토리에 추가되었습니다.
7. crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166/ 위치에서 터미널을 엽니다.
8. 아래 명령을 사용하여 node_modules 디렉토리 삭제

   **rm -rf node_modules**

9. 아래 명령을 사용하여 node_modules.zip 압축 해제

   **unzip node_modules.zip**

10. unzip 명령이 설치/인식되지 않으면 다음 명령을 사용하여 설치할 수 있습니다

   **yum install unzip**

11. fontconfig 패키지를 설치합니다.
명령: yum install fontconfig
12. 웹 편집기에서 사전 설정에서 기본 PDF을 생성합니다.

**참고** : node_modules.zip 패키지를 다운로드할 수 있습니다 [여기](https://acrobat.adobe.com/link/track?uri=urn:aaid:scds:US:295d8f03-41e1-429b-8465-2761ce3c2fb3).

Linux 운영 체제용 다운로드한 노드 모듈을 수동으로 가져오는 것은 안내서 4.1 또는 이전 버전을 사용하는 사용자를 위한 해결 방법입니다.

## Mac 시스템의 구성 단계(JAVA 11/8)

1. oracle JAVA 11 또는 Oracle JAVA 8을 설치합니다.
2. JAVA_HOME 환경 변수를 설치된 JAVA 디렉토리로 설정합니다.
3. Unix 셸을 엽니다.
Bash는 구성을 설정하는 데 사용됩니다.

   명령: nano ~/.bashrc

4. 설치된 Java 버전을 기준으로 아래 명령을 사용하여 JAVA_HOME 변수를 설정합니다.

   예:

   JAVA 11:

   export JAVA\_HOME= /Library/Java/JavaVirtualMachines/jdk-11.0.15.1.jdk/Contents/Home

5. 기본 로드

   명령: source ~/.bashrc.

6. 명령 echo $JAVA_HOME을 사용하여 JAVA_HOME이 설정되었는지 확인합니다.

7. AEM 설치 경로에서 아래의 세 가지 명령을 실행합니다.

   C:/{aem-installation-folder}/crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166

   i) 를 찾습니다. -type d -exec chmod 0755 {} \; ii) 를 찾습니다. -type f -exec chmod 0755 {} \; iii) ./node-darwin/bin/node node-darwin/lib/node_modules/npm/bin/npm-cli.js —prefix . install —unsafe-perm —scripts-prepend-node-path

8. 아래 명령을 사용하여 Java가 설치되어 있는지 확인합니다.

   i) 실행 **./node-darwin/bin/node** /crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166 폴더에서 명령

   ![mac](../assets/publishing/mac.png)

   ii) a = require(&#39;java&#39;)

9. fontconfig 패키지를 설치합니다.
명령: apt 설치 fontconfig

10. 웹 편집기에서 사전 설정에서 기본 PDF을 생성합니다.

## 문제 해결

다음은 환경 변수가 제대로 설정되지 않은 경우 PDF 생성 중에 발생할 수 있는 일반적인 오류입니다.

### Windows/Mac OS에서 Null 포인터 예외

![null 포인터 예외](../assets/publishing/null-pointer-exception.png)

### RHEL 7 Linux OS에서 누락된 라이브러리

![누락된 라이브러리](../assets/publishing/missing-libraries.png)

위의 단계를 수행하는 동안 문제가 발생하는 경우 AEM 안내서 커뮤니티에 질문을 게시하십시오 [포럼](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation) 지원 요청.
