---
title: AEM Guides as a Cloud Service에 대한 새로운 마이크로서비스 기반 게시 구성
description: AEM Guides의 새로운 마이크로서비스 기반 게시를 구성하는 방법에 대해 알아봅니다.
source-git-commit: c2981b5635353eb84c9e46a03de1b1ed07aa5bf3
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# AEM Guides as a Cloud Service에 대한 새로운 마이크로서비스 기반 게시 구성

새로운 게시 마이크로서비스를 통해 사용자는 AEM as a Cloud Service Guides에서 동시에 대규모 게시 워크로드를 실행할 수 있으며 업계 최고의 Adobe I/O Runtime 서버리스 플랫폼을 활용할 수 있습니다.

각 게시 요청에 대해 AEM Guides는 사용자 요청에 따라 가로로 확장되는 별도의 컨테이너를 as a Cloud Service으로 실행합니다. 이를 통해 사용자는 여러 게시 요청을 실행하고 대형 온프레미스 AEM 서버보다 더 나은 성능을 얻을 수 있습니다.

새로운 클라우드 게시 서비스는 Adobe IMS JWT 기반 인증을 통해 보호되므로 고객은 아래 단계에 따라 환경을 Adobe의 보안 토큰 기반 인증 워크플로와 통합하고 새로운 클라우드 기반의 확장 가능한 게시 솔루션을 사용해야 합니다.


## Adobe Developer 콘솔에서 IMS 구성 만들기

**혼동을 만드는 데 필요한 역할**: 시스템 관리자

Adobe Developer 콘솔에서 IMS 구성을 만들려면 다음 단계를 수행하십시오.

1. Developer Console을 엽니다. `https://developer.adobe.com/console`.

1. 다음으로 전환 **프로젝트** 맨 위에 있는 탭입니다.

   <img src="assets/projects-tab.png" alt="프로젝트 탭" width="500">

1. 새 빈 프로젝트를 만들려면 **빈 프로젝트** 다음에서 **새 프로젝트 만들기** 드롭다운입니다.

   <img src="assets/create-new-project.png" alt="새 프로젝트 만들기" width="500">

1. 선택 **API** 다음에서 **프로젝트에 추가** 프로젝트에 IO Management API를 추가하는 드롭다운입니다.

   <img src="assets/add-project.png" alt="프로젝트 추가" width="300">

   <img src="assets/io-management-api.png" alt="io 관리" width="500">

1. API를 추가하는 동안 새 개인/공개 키 쌍을 만듭니다. 이렇게 하면 시스템에 개인 키가 자동으로 다운로드됩니다.

   <img src="assets/generate-key-pair.png" alt="키 쌍 생성" width="500">

1. 구성된 API를 저장합니다.

   <img src="assets/save-api.png" alt="api 저장" width="600">

1. 다음으로 돌아가기: **프로젝트** tab 키를 누른 다음 클릭 **프로젝트 개요** 왼쪽이요

   <img src="assets/project-overview.png" alt="프로젝트 개요" width="500">

1. 클릭 **다운로드** 서비스 JSON을 다운로드하려면 맨 위에 있는 버튼을 클릭합니다.

   <img src="assets/download-json.png" alt="json 다운로드" width="500">

이제 JWT 인증 세부 사항을 구성했으며 개인 키 및 서비스 세부 사항 JSON도 다운로드했습니다. 다음 섹션에서 이 두 파일을 필요로 하므로 이 두 파일을 가까이에 두십시오.

### 환경에 IMS 구성 추가

다음 단계를 수행하여 환경에 IMS 구성을 추가합니다.

1. Experience manager를 열고 구성할 환경이 포함된 프로그램을 선택합니다.
1. 다음으로 전환 **환경** 탭.
1. 구성할 환경 이름을 클릭합니다. 환경 정보 페이지로 이동합니다.
1. 다음으로 전환 **구성** 탭.
1. 아래 스크린샷과 같이 개인 키 및 프로젝트 JSON을 업로드합니다. 아래에 강조 표시된 것과 동일한 이름 및 구성을 사용하고 있는지 확인하십시오.

   <img src="assets/ims-config-environment.png" alt="ims 구성" width="500">

>[!NOTE]
>
> 위 스크린샷과 같이 개인 키 및 서비스 세부 사항 JSON 파일의 컨텐츠를 열고 복사한 다음 구성 패널의 값 열에 붙여넣어야 합니다.

환경에 IMS 구성을 추가한 후 다음 단계를 수행하여 OSGi를 사용하여 이러한 속성을 AEM Guides와 연결합니다.

1. Cloud Manager Git 프로젝트 코드에서 아래에 주어진 두 개의 파일을 추가합니다(파일 콘텐츠의 경우 참조). [부록](#appendix)).

   * `com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`
   * `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService.xml`
1. 새로 추가된 파일에 다음이 적용되는지 확인합니다. `filter.xml`.
1. Git 변경 사항을 커밋하고 푸시합니다.
1. 파이프라인을 실행하여 환경에 변경 사항을 적용합니다.

이 작업이 완료되면 새로운 마이크로서비스 기반 클라우드 게시를 사용할 수 있습니다.

## 부록 {#appendix}

**파일**:
`com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`

**콘텐츠**:

```
{
  "service.account.details": "$[secret:SERVICE_ACCOUNT_DETAILS]",
  "private.key": "$[secret:PRIVATE_KEY]"
}
```

**파일**: `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService.xml`

**콘텐츠**:

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          jcr:primaryType="sling:OsgiConfig"
          dxml.publish.microservice.url="https://adobeioruntime.net/api/v1/web/543112-guidespublisher/default/publishercaller.json"
          dxml.use.publish.microservice="{Boolean}true"
/>
```