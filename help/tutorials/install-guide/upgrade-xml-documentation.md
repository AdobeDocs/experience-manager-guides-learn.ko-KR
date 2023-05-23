---
title: Adobe Experience Manager Guides 업그레이드
description: Adobe Experience Manager Guides를 업그레이드하는 방법 알아보기
source-git-commit: 629a3714e7b75af609238a506688da2674bf31cc
workflow-type: tm+mt
source-wordcount: '2750'
ht-degree: 1%

---


# Adobe Experience Manager Guides 업그레이드 {#id224MBE0M0XA}

>[!NOTE]
>
> 사용 허가된 제품 버전에 맞는 업그레이드 지침을 따르십시오.

현재 버전의 AEM Guides를 버전 4.2.1로 업그레이드할 수 있습니다
- 버전 4.1, 4.1.x 또는 4.2를 사용하는 경우 버전 4.2.1로 바로 업그레이드할 수 있습니다.
- 버전 4.0을 사용 중인 경우 버전 4.2.1로 업그레이드하기 전에 버전 4.2로 업그레이드해야 합니다.
- 버전 3.8.5를 사용하는 경우 버전 4.2로 업그레이드하기 전에 버전 4.0으로 업그레이드해야 합니다.
- 3.8.5 이전 버전을 사용하는 경우 제품별 설치 안내서에서 업그레이드 AEM 안내서 섹션을 참조하십시오.

>[!NOTE]
>
> AEM Guides 버전을 업그레이드하기 전에 AEM 서비스 팩을 설치해야 합니다.

자세한 내용은 다음 절차를 참조하십시오.

- [3.8.5에서 버전 4.0으로 업그레이드](#id2256DK003E1)
- [버전 4.2로 업그레이드](#id22A3F500SXA)
- [버전 4.2.1로 업그레이드](#upgrade-version-4-2-1)


>[!IMPORTANT]
>
> 업그레이드를 시작하기 전에 전체 시스템 백업을 수행하여 데이터 손실을 방지하십시오.

## 버전 3.8.5에서 버전 4.0으로 업그레이드 {#id2256DK003E1}

AEM Guides 버전 3.8.5를 사용하는 경우 AEM Guides 버전 4.0으로 업그레이드할 수 있습니다. 업그레이드 기능을 사용하면 이전 버전의 AEM Guides를 제거할 필요가 없습니다.

프로세스를 실행하기 전에 완료해야 하는 특정 작업이 있습니다. 다음 하위 섹션에서는 사전 요구 사항, 보고서 생성 및 마이그레이션 프로세스를 안내합니다. 또한 AEM Guides 버전 4.0을 설치한 후 고객 설정에 따라 다양한 구성을 사용자 지정할 수 있습니다.

>[!NOTE]
>
> 이 업그레이드 프로세스는 버전 3.8.5에서 버전 4.0으로만 적용할 수 있습니다. 버전 3.4 이상에서 3.8.5로 업그레이드하는 절차는 *AEM Guides 업그레이드* 에 있는 제품별 설치 안내서의 섹션 [도움말 보관 페이지](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html).

****전제 조건****

AEM Guides 업그레이드 프로세스를 시작하기 전에 다음을 확인하십시오.

1. 검토를 위해 열려 있는 항목의 검토 주석을 가져왔습니다.
1. 모든 활성 검토를 닫았습니다.
1. 모든 번역 작업을 마감했습니다.
1. AEM Guides의 이전 버전 \(주 릴리스 또는 패치 릴리스\) 맨 위에 설치된 AEM Guides 핫픽스를 제거합니다.

**버전 4.0을 설치하기 전에**

버전 4.0을 설치하기 전에 다음 단계를 수행하십시오.

1. 이 시점에서 AEM Guides 가 버전 3.8.5에 있는지 확인합니다.
1. 업그레이드 스크립트 패키지를 다운로드합니다. 이렇게 하려면 다음에서 &quot;XML Documentation 솔루션 4.0 업그레이드 패키지&quot;를 검색합니다. [Adobe 소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) zip 파일을 다운로드합니다.
1. 패키지 관리자를 통해 AEM에 이 패키지를 업로드하고 이 패키지를 설치합니다.
1. 업그레이드 패키지가 설치되면 아래의 지정된 스크립트를 동일한 순서로 실행하고 지정된 지침을 따릅니다.

**업그레이드 호환성 API 확인**

이 API는 현재 시스템 상태를 평가하고 업그레이드가 가능한지 여부를 보고하도록 설계되었습니다. 이 스크립트를 실행하려면 아래의 특정 끝점을 트리거합니다.

|끝점|/bin/dxml/upgrade/3xto4x/report| |요청 유형|**GET** 관리자로 AEM 인스턴스에 로그인한 웹 브라우저를 사용할 수 있습니다.| |예상 응답|- 필요한 모든 노드를 이동할 수 있는 경우 합격 확인이 이루어집니다. <br>- 대상 위치에 노드가 있는 경우 관련 오류가 발생합니다. 저장소 \(노드 /var/dxml\ 삭제)를 정리하고 업그레이드 패키지를 다시 설치한 다음 이 끝점을 다시 트리거합니다. <br>**참고:** 이는 3.x AEM Guides에서 타겟 위치를 이전에 사용하지 않았기 때문에 일반적인 오류가 아닙니다. <br> - 이 스크립트가 성공하지 못할 경우 진행하지 말고 고객 성공 팀에 보고하십시오.|

**시스템 데이터 마이그레이션 API**

이 API는 다음에 언급된 대로 시스템 데이터를 마이그레이션하도록 설계되었습니다. [마이그레이션 매핑](#id2244LE040XA) 섹션.

1. 업그레이드 호환성 확인 API에 실패한 경우 이 스크립트를 실행하지 마십시오\(계속 진행하지 마십시오\).
1. 업그레이드 호환성 확인 API가 성공을 반환하면 업그레이드 스크립트를 실행할 수 있습니다.

|끝점|/bin/dxml/upgrade/3xto4x| |요청 유형|**POST** 이 스크립트는 POST 요청이므로 Postman과 같은 에이전트를 통해 실행해야 합니다.| |예상 응답|- 마이그레이션에 성공하면 XML Documentation 솔루션 버전 4.0을 설치할 수 있습니다.<br>- 오류가 있는 경우 마지막 체크포인트로 복원하고 API 출력과 함께 오류 로그를 고객 성공 팀과 공유합니다.|

**마이그레이션 매핑**: 위의 API는 소스 위치 아래의 모든 데이터를 타겟 위치로 마이그레이션합니다.

| 소스 | 대상 |
|------|------|
| /content/fmdita | /var/dxml |
| /content/dxml | /var/dxml |
| /etc/fmdita | /libs/fmdita |

## 버전 4.0 설치 {#id23598G006XA}

1. 업그레이드 단계가 성공한 경우에만 버전 4.0을 설치합니다.
1. 에서 4.0 버전 패키지 다운로드 [Adobe 소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html):

   - 소프트웨어의 UUID 버전을 사용하는 경우 &quot;AEM 6.5용 XML Documentation 솔루션용 4.0 UUID 릴리스&quot;를 검색합니다.
   - XML Documentation 비 UUID 버전의 소프트웨어를 사용하는 경우 &quot;4.0 Non-UUID Release for AEM 6.5&quot;를 검색합니다.
CRX 패키지 관리자를 사용하여 기존 AEM 서버 인스턴스에 패키지를 업로드하고 설치합니다.

   >[!NOTE]
   >
   > 모든 시스템 구성 요소가 시작될 때까지 기다립니다.

1. 패키지를 설치한 후 브라우저 캐시를 지웁니다.
1. Dispatcher가 AEM 작성자 인스턴스에 구성된 경우 다음 단계를 수행합니다.
   - Dispatcher 규칙에서 다음 사항이 처리되는지 확인합니다.
   - URL 패턴 /home/users/\*/preferences가 허용 목록에 추가되었습니다.
   - URL 패턴 /libs/cq/security/userinfo.json 이 캐시되지 않습니다.
1. Dispatcher 캐시 지우기 \ `clientlibs` 캐시됨\).

## 버전 4.2로 업그레이드 {#id22A3F500SXA}

버전 4.2로 업그레이드하는 방법은 현재 버전의 AEM Guides에 따라 다릅니다.

버전 4.0, 4.1 또는 4.1.x를 사용하는 경우 버전 4.2로 바로 업그레이드할 수 있습니다.

****전제 조건****

AEM Guides 4.2 업그레이드 프로세스를 시작하기 전에 다음을 확인하십시오.

1. AEM Guides 버전 4.0, 4.1 또는 4.1.x로 업그레이드되었습니다.
1. 모든 번역 작업을 마감했습니다.
1. 로그 수준을 (으)로 변경함 **정보** 대상 `com.adobe.fmdita.translationservices.TranslationMapUpgradeScript` 클래스를 만들고 새 로그 파일에 이러한 로그를 추가합니다. 예: `logs/translation_upgrade.log.`

>[!NOTE]
>
> 모든 활성 리뷰를 닫아야 합니다. 4.2로 업그레이드하는 동안 검토 작업이 닫히지 않으면 진행 중인 이전 검토 작업이 이전 검토 페이지에서 사용자를 계속 사용하게 되며 업그레이드 후 생성된 검토 작업에는 기능의 최신 업데이트가 표시됩니다.

## 버전 4.2 설치 {#id2245IK0E0EV}

1. 에서 4.2 버전 패키지 다운로드 [Adobe 소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
1. 버전 4.2 패키지를 설치합니다.
1. 패키지 설치를 완료한 후 로그에서 다음 메시지를 기다립니다.

   `Completed the post deployment setup script`

   위의 메시지는 설치 단계가 모두 완료되었음을 나타냅니다.

   다음 오류 접두사가 발생하면 고객 성공 팀에 보고하십시오.

   - 배포 후 설정 스크립트 오류
   - 번역 맵을 포팅하는 동안 예외 발생
   - v1에서 v2로의 번역 맵을 속성에 대해 포트할 수 없음
1. 필요한 경우 버전 4.2와 함께 릴리스된 Oxygen 커넥터 플러그인을 업그레이드하십시오.
1. 패키지를 설치한 후 브라우저 캐시를 지웁니다.
1. 다음 섹션에 자세히 설명된 대로 맞춤화를 계속 업그레이드하십시오.

## 버전 4.2를 설치한 후 {#id2326F02004K}

>[!IMPORTANT]
>
> 업그레이드된 서버에 하이 테크 템플릿이 표시되지 않습니다. 서버에 하이 테크 템플릿을 포함하려면 다음을 복사합니다. 소스: /libs/fmdita/pdf/하이 테크 대상: /content/dam/dita-templates/pdf

AEM Guides를 설치한 후 새로 설치한 버전에서 설정에 적용할 수 있는 다양한 구성을 병합할 수 있습니다.

>[!NOTE]
>
> dam-update-asset 모델은 맞춤화될 수 있다. 따라서 사용자 정의가 수행된 경우 사용자 정의 및 AEM Guides를 모델의 작업 복사본에 동기화해야 합니다.

1. **DAM 자산 업데이트 워크플로우 \(변경 후 처리\):**

1. URL 열기:

   ```http
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html
   ```

1. 선택 **DAM 자산 업데이트 워크플로우**.
1. 클릭 **편집**.
1. 다음과 같은 경우 **DXML 사후 프로세스 개시자** 구성 요소가 있습니다. 맞춤화가 동기화되었는지 확인하십시오.
1. 다음과 같은 경우 **DXML 사후 프로세스 개시자** 구성 요소가 없습니다. 다음 단계를 수행하여 구성 요소를 삽입하십시오.

1. 클릭 **구성 요소 삽입** \(프로세스의 마지막 단계로 AEM Guides 후처리를 담당합니다\).
1. 구성 **프로세스 단계** 아래 세부 정보:

   **공통 탭**

   **제목:** DXML 사후 프로세스 개시자

   **설명**: 수정/생성된 에셋의 DXML 사후 처리를 위해 슬링 작업을 트리거하는 DXML 사후 프로세스 개시자 단계입니다

   **프로세스 탭**

   - 선택 **DXML 사후 프로세스 개시자**&#x200B;다음에서 **프로세스** 드롭다운

   - 선택 **핸들러 진행**

   - 선택 **완료**

1. 클릭 **동기화** 변경 작업을 완료한 후 오른쪽 상단에서 를 클릭합니다. 성공 알림을 받게 됩니다.

   >[!NOTE]
   >
   > 새로 고침하여 맞춤화된 변경 사항 및 AEM Guides 사후 처리 단계가 최종 워크플로우 모델에 있는지 확인합니다.

1. 한 번 **DAM 자산 업데이트 워크플로우**&#x200B;이(가) 확인되었습니다. 해당 런처 구성을 확인하십시오. 이렇게 하려면 AEM Workflow 인터페이스로 이동하여 런처를 엽니다.

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   필요한 경우\ 다음에 해당하는 두 개의 런처 \(활성 상태여야 함\)를 찾아서 변경합니다. **DAM 자산 업데이트 워크플로우**:

1. &quot; 런처&#x200B;*노드가 생성됨*&#x200B;다음에 대한 &quot; **DAM 자산 업데이트 워크플로우**- 조건 `"jcr:content/jcr:mimeType!=video"`, &#39;Globbing&#39; 값은 다음과 같아야 합니다.

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39;에는 `"event-user-data:changedByWorkflowProcess"`.
   - &quot; 런처&#x200B;*노드가 수정됨*&#x200B;다음에 대한 &quot; **DAM 자산 업데이트 워크플로우 -** 조건 용`jcr:content/jcr:mimeType!=video`&quot;,
   - 
      - &#39;Globbing&#39; 값은 다음과 같아야 합니다.

   ```json
   `"/content/dam(/((?!/subassets|/translation_output).)*/)renditions/original"`
   ```

   - &#39;excludeList&#39;에는 `"event-user-data:changedByWorkflowProcess"`.
1. 업그레이드가 완료되면 사용자 지정/오버레이가 새 애플리케이션 코드와 일치하도록 확인 및 업데이트되었는지 확인합니다. 다음은 몇 가지 예입니다.
   - /libs/fmditaor/libsfrom에서 오버레이된 모든 구성 요소는 새 제품 코드와 비교해야 하며, 업데이트는 / 앱에서 오버레이된 파일에서 수행해야 합니다.
   - 제품에서 사용되는 모든 clientlib 카테고리는 변경 사항을 검토해야 합니다. 최신 기능을 가져오려면 재정의된 모든 구성 \(아래 예제\)을 최신 구성과 비교해야 합니다.
   - elementmapping.xml
   - ui\_config.json\(폴더 프로필에 설정되었을 수 있음\)
   - 수정됨 `com.adobe.fmdita.config.ConfigManager`
   - 사용자 지정 코드에서 이전 경로 \(에 언급된 대로)를 사용하고 있는지 확인합니다. [마이그레이션 매핑](#id2244LE040XA) section\) - 맞춤화가 예상대로 작동하도록 새 경로로 업데이트해야 합니다.
1. 현재 릴리스에 포함된 새 구성에 대해 읽어 보십시오. \(check [릴리스 정보](../release-info/release-notes-4.2.md)\) 기능에 영향을 미치는지 확인한 다음 적절한 조치를 취하십시오. 예를 들어 버전 4.0에 도입된 &quot;향상된 파일 및 버전 처리&quot;를 사용하는 것이 좋습니다. 이 경우 구성을 활성화해야 합니다.

## 새 찾기 및 바꾸기를 사용할 기존 콘텐츠를 색인화하는 단계:

기존 콘텐츠를 색인화하기 위해 다음 단계를 수행하고 맵 수준에서 새 찾기 및 바꾸기 텍스트를 사용합니다.

- 올바른 인증을 사용하여 서버에 대한 POST 요청 실행\ - `http://<server:port\>/bin/guides/map-find/indexing`. \(선택 사항: 맵의 특정 경로를 전달하여 인덱싱할 수 있습니다. 기본적으로 모든 맵은 인덱싱됩니다. \|\| 예: `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`\)

- API는 jobId를 반환합니다. 작업 상태를 확인하려면 작업 ID가 있는 GET 요청을 동일한 끝점으로 보낼 수 있습니다. `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\(예: `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\)

- 작업이 완료되면 위의 GET 요청은 성공으로 응답하고 맵이 실패한 경우 언급됩니다. 인덱싱된 맵은 서버 로그에서 확인할 수 있습니다.

## 버전 4.2.1로 업그레이드 {#upgrade-version-4-2-1}

버전 4.2.1로 업그레이드하는 방법은 현재 버전의 AEM Guides에 따라 다릅니다.

버전 4.1, 4.1.x 또는 4.2를 사용하는 경우 버전 4.2.1로 바로 업그레이드할 수 있습니다.

>[!NOTE]
>
>사후 처리 및 인덱싱에는 몇 시간이 걸릴 수 있습니다. 사용량이 적은 시간 동안 업그레이드 프로세스를 시작하는 것이 좋습니다.

****전제 조건****

AEM Guides 4.2.1 업그레이드 프로세스를 시작하기 전에 다음을 확인하십시오.

1. AEM Guides 버전 4.1, 4.1.x 또는 4.2로 업그레이드되었습니다.
1. 모든 번역 작업을 마감했습니다.
1. 로그 수준을 (으)로 변경함 **정보** 대상 `com.adobe.fmdita.translationservices.TranslationMapUpgradeScript` 클래스를 만들고 새 로그 파일에 이러한 로그를 추가합니다. 예: `logs/translation_upgrade.log.`

>[!NOTE]
>
> 모든 활성 리뷰를 닫아야 합니다. 4.2로 업그레이드하는 동안 검토 작업이 닫히지 않으면 진행 중인 이전 검토 작업이 이전 검토 페이지에서 사용자를 계속 사용하게 되며 업그레이드 후 생성된 검토 작업에는 기능의 최신 업데이트가 표시됩니다.

## 버전 4.2.1 설치

1. 에서 4.2.1 버전 패키지 다운로드 [Adobe 소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
1. 버전 4.2.1 패키지를 설치합니다.
1. 트리거를 적중하여 번역 맵 업그레이드 작업을 시작하도록 선택할 수 있습니다. 자세한 내용은 [서블릿을 통한 스크립트 트리거 활성화](#enable-trigger-serverlet).


1. 패키지 설치를 완료한 후 로그에서 다음 메시지를 기다립니다.

   `Completed the post deployment setup script`

   위의 메시지는 설치 단계가 모두 완료되었음을 나타냅니다.

   다음 오류 접두사가 발생하면 고객 성공 팀에 보고하십시오.

   - 배포 후 설정 스크립트 오류
   - 번역 맵을 포팅하는 동안 예외 발생
   - v1에서 v2로의 번역 맵을 속성에 대해 포트할 수 없음
1. 필요한 경우 버전 4.2와 함께 릴리스된 Oxygen 커넥터 플러그인을 업그레이드하십시오.
1. 패키지를 설치한 후 브라우저 캐시를 지웁니다.
1. 다음 섹션에 자세히 설명된 대로 맞춤화를 계속 업그레이드하십시오.

### 서블릿을 통한 스크립트 트리거 활성화{#enable-trigger-serverlet}

POST:

```
http://localhost:4503/bin/guides/script/start?jobType=translation-map-upgrade
```

응답:

```
{
"msg": "Job is successfully submitted and lock node is created for future reference",
"lockNodePath": "/var/dxml/executor-locks/translation-map-upgrade/1683190032886",
"status": "SCHEDULED"
}
```

위의 응답 JSON에서 키 `lockNodePath` 제출된 작업을 가리키는 저장소에 생성된 노드로의 경로를 유지합니다. 작업이 완료되면 자동으로 삭제되며, 그때까지 이 노드를 참조하여 작업의 현재 상태를 확인할 수 있습니다.

샘플 로그: 다음은 스크립트를 트리거한 후 로그 파일에 표시되는 로그 샘플입니다.

```
04.05.2023 14:17:12.876 *INFO* [[0:0:0:0:0:0:0:1] [1683190032736] POST /bin/guides/script/start HTTP/1.1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Acquiring lock for job : translation-map-upgrade
04.05.2023 14:17:12.897 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Starting the thread to upgrade translation map from V1 to V2
04.05.2023 14:17:12.899 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Initiating lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.901 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Starting porting of translation map from V1 to V2
04.05.2023 14:17:12.904 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Memory increase is of : 764 kB
04.05.2023 14:17:12.906 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2
04.05.2023 14:17:12.907 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Releasing lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.909 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2
```

다음을 찾습니다. `com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2` 및 `com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2` 다음 단계로 진행하기 전에



## 버전 4.2.1을 설치한 후

>[!IMPORTANT]
>
> 업그레이드된 서버에 하이 테크 템플릿이 표시되지 않습니다. 서버에 하이 테크 템플릿을 포함하려면 다음을 복사합니다. 소스: /libs/fmdita/pdf/하이 테크 대상: /content/dam/dita-templates/pdf

AEM Guides를 설치한 후 새로 설치한 버전에서 설정에 적용할 수 있는 다양한 구성을 병합할 수 있습니다.

>[!NOTE]
>
> dam-update-asset 모델은 맞춤화될 수 있다. 따라서 사용자 정의가 수행된 경우 사용자 정의 및 AEM Guides를 모델의 작업 복사본에 동기화해야 합니다.

1. **DAM 자산 업데이트 워크플로우 \(변경 후 처리\):**

1. URL 열기:

   ```http
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html
   ```

1. 선택 **DAM 자산 업데이트 워크플로우**.
1. 클릭 **편집**.
1. 다음과 같은 경우 **DXML 사후 프로세스 개시자** 구성 요소가 있습니다. 맞춤화가 동기화되었는지 확인하십시오.
1. 다음과 같은 경우 **DXML 사후 프로세스 개시자** 구성 요소가 없습니다. 다음 단계를 수행하여 구성 요소를 삽입하십시오.

1. 클릭 **구성 요소 삽입** \(프로세스의 마지막 단계로 AEM Guides 후처리를 담당합니다\).
1. 구성 **프로세스 단계** 아래 세부 정보:

   **공통 탭**

   **제목:** DXML 사후 프로세스 개시자

   **설명**: 수정/생성된 에셋의 DXML 사후 처리를 위해 슬링 작업을 트리거하는 DXML 사후 프로세스 개시자 단계입니다

   **프로세스 탭**

   - 선택 **DXML 사후 프로세스 개시자**&#x200B;다음에서 **프로세스** 드롭다운

   - 선택 **핸들러 진행**

   - 선택 **완료**

1. 클릭 **동기화** 변경 작업을 완료한 후 오른쪽 상단에서 를 클릭합니다. 성공 알림을 받게 됩니다.

   >[!NOTE]
   >
   > 새로 고침하여 맞춤화된 변경 사항 및 AEM Guides 사후 처리 단계가 최종 워크플로우 모델에 있는지 확인합니다.

1. 한 번 **DAM 자산 업데이트 워크플로우**&#x200B;이(가) 확인되었습니다. 해당 런처 구성을 확인하십시오. 이렇게 하려면 AEM Workflow 인터페이스로 이동하여 런처를 엽니다.

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   필요한 경우\ 다음에 해당하는 두 개의 런처 \(활성 상태여야 함\)를 찾아서 변경합니다. **DAM 자산 업데이트 워크플로우**:

1. &quot; 런처&#x200B;*노드가 생성됨*&#x200B;다음에 대한 &quot; **DAM 자산 업데이트 워크플로우**- 조건 `"jcr:content/jcr:mimeType!=video"`, &#39;Globbing&#39; 값은 다음과 같아야 합니다.

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39;에는 `"event-user-data:changedByWorkflowProcess"`.
   - &quot; 런처&#x200B;*노드가 수정됨*&#x200B;다음에 대한 &quot; **DAM 자산 업데이트 워크플로우 -** 조건 용`jcr:content/jcr:mimeType!=video`&quot;, &#39;Globbing&#39; 값은 다음과 같아야 합니다.

   ```json
   `"/content/dam(/((?!/subassets|/translation_output).)*/)renditions/original"`
   ```

   - `excludeList` 이(가) 있어야 함 `"event-user-data:changedByWorkflowProcess"`.


1. 업그레이드가 완료되면 사용자 지정/오버레이가 새 애플리케이션 코드와 일치하도록 확인 및 업데이트되었는지 확인합니다. 다음은 몇 가지 예입니다.
   - /libs/fmditaor/libsfrom에서 오버레이된 모든 구성 요소는 새 제품 코드와 비교해야 하며, 업데이트는 / 앱에서 오버레이된 파일에서 수행해야 합니다.
   - 제품에서 사용되는 모든 clientlib 카테고리는 변경 사항을 검토해야 합니다. 최신 기능을 가져오려면 재정의된 모든 구성 \(아래 예제\)을 최신 구성과 비교해야 합니다.
   - elementmapping.xml
   - ui\_config.json\(폴더 프로필에 설정되었을 수 있음\)
   - 수정됨 `com.adobe.fmdita.config.ConfigManager`
   - 사용자 지정 코드에서 이전 경로 \(에 언급된 대로)를 사용하고 있는지 확인합니다. [마이그레이션 매핑](#id2244LE040XA) section\) - 맞춤화가 예상대로 작동하도록 새 경로로 업데이트해야 합니다.
1. 현재 릴리스에 포함된 새 구성에 대해 읽어 보십시오. \(check [릴리스 정보](../release-info/release-notes-4.2.1.md)\) 기능에 영향을 미치는지 확인한 다음 적절한 조치를 취하십시오. 예를 들어 버전 4.0에 도입된 &quot;향상된 파일 및 버전 처리&quot;를 사용하는 것이 좋습니다. 이 경우 구성을 활성화해야 합니다.

## 새 찾기 및 바꾸기를 사용할 기존 콘텐츠를 색인화하는 단계:

기존 콘텐츠를 색인화하기 위해 다음 단계를 수행하고 맵 수준에서 새 찾기 및 바꾸기 텍스트를 사용합니다.

- 다음을 확인합니다. `damAssetLucene` 색인화가 완료되었습니다. 서버에 있는 데이터의 양에 따라 최대 몇 시간이 소요될 수 있습니다. 리인덱싱 필드가 false로 설정되어 있는지 확인하여 리인덱싱이 완료되었는지 확인할 수 있습니다
   `http://<server:port>/oak:index/damAssetLucene`.  또한에서 사용자 지정을 추가한 경우 `damAssetLucene`, 다시 적용해야 할 수 있습니다.

- 올바른 인증을 사용하여 서버에 대한 POST 요청 실행\ - `http://<server:port\>/bin/guides/map-find/indexing`. (선택 사항: 맵의 특정 경로를 전달하여 인덱싱할 수 있습니다. 기본적으로 모든 맵은 \|\| 예를 들면 다음과 같습니다. `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- 루트 폴더를 전달하여 특정 폴더(및 그 하위 폴더)의 DITA 맵을 인덱싱할 수도 있습니다. 예, `http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`. paths 매개 변수와 root 매개 변수가 모두 전달되면 paths 매개 변수만 고려됩니다.

- API는 jobId를 반환합니다. 작업 상태를 확인하려면 작업 ID가 있는 GET 요청을 동일한 끝점으로 보낼 수 있습니다. `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\(예: `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\)


- 작업이 완료되면 위의 GET 요청은 성공으로 응답하고 맵이 실패한 경우 언급됩니다. 인덱싱된 맵은 서버 로그에서 확인할 수 있습니다.

**상위 항목:**[&#x200B;다운로드 및 설치](download-install.md)
