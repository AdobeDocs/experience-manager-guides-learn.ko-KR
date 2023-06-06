---
title: 비 UUID에서 UUID로의 콘텐츠 마이그레이션
description: UUID가 아닌 콘텐츠를 UUID로 마이그레이션하는 방법 알아보기
exl-id: 093b380e-9a8b-4e60-aeaa-3458e8c257f2
source-git-commit: 21edbb2f8a49213ea95fac8a957056711219e7e4
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# 비 UUID에서 UUID로의 콘텐츠 마이그레이션 {#id226TI0U20XA}

>[!IMPORTANT]
>
> UUID가 아닌 콘텐츠를 UUID 서버로 마이그레이션할 수 있습니다. UUID 서버로 마이그레이션하려면 AEM guides 버전 4.0이 설치된 비 UUID 서버가 있어야 합니다.

UUID가 아닌 콘텐츠를 마이그레이션하려면 다음 단계를 수행하십시오.

>[!NOTE]
>
> 각 단계는 매우 중요하며, 단계를 누락하면 서버 데이터가 실패하거나 손상될 수 있습니다. 모든 단계를 완료했는지 확인합니다.

1. 다음을 확인합니다. **사후 처리 워크플로 런처 활성화** 위치: *com.adobe.fmdita.config.ConfigManager* 및 **버전 사후 처리 활성화** 위치: *com.adobe.fmdita.postprocess.version.PostProcessVersionObservation* 활성화되었습니다.

   ```http
   http://<server name>:<port>/system/console/configMgr/com.adobe.fmdita.config.ConfigManager
   ```

1. UUID가 아닌 버전에 대해 다음 주요 릴리스의 UUID 버전을 설치합니다. 예를 들어 4.0 비 UUID 빌드를 사용하는 경우 UUID 버전 4.1을 설치해야 합니다.

1. 런처 탭에서 다음 워크플로 및 /content/dam에서 런처를 사용하여 실행되는 기타 워크플로를 비활성화합니다. `http://localhost:4502/libs/cq/workflow/content/console.html`:

   - **DAM 자산 업데이트** 워크플로우
   - **DAM 메타데이터 원본에 쓰기** 워크플로우

1. 사용 안 함 **사후 처리 워크플로 런처 활성화** 위치: *com.adobe.fmdita.config.ConfigManager* 및 비활성화 **버전 사후 처리 활성화** 위치: *com.adobe.fmdita.postprocess.version.PostProcessVersionObservation*.

   ```http
   http://<server name>:<port>/system/console/configMgr/com.adobe.fmdita.config.ConfigManager
   ```

1. 다음에 대한 별도의 로거 추가 `com.adobe.fmdita.uuid.upgrade.UuidUpgrade.`

   브라우저 응답은 /content/uuid-upgrade/logs에서도 사용할 수 있습니다.

1. 이 있는 더 작은 데이터가 있는 폴더에서 주어진 쿼리를 실행합니다. `doReviews=false` / content/dam에서 실행하기 전에: `http://localhost:4502/bin/dxml/uuid_upgrade?root=/content/dam/test&doReviews=false`

   >[!TIP]
   >
   >  폴더의 모든 파일이 제대로 업그레이드되고 해당 폴더에만 모든 기능이 작동하는지 확인할 수 있습니다.

**쿼리에 대한 매개 변수:**

    - &#39;root&#39;: 업그레이드가 수행되어야 하는 루트 폴더 \(모든 저장소에 /content/dam 사용).\)
    - &#39;doReviews&#39;: true/false \(검토를 업그레이드해야 하는 경우). 기본값은 false입니다.\)
    - &#39;doBaselines&#39;: true/false \(기준선을 업그레이드해야 하는 경우 또는 업그레이드하지 않는 경우). 기본값은 true입니다.\)
    - &#39;processLevel&#39;: -1\(복원 없이 실패\), 0\(복원 실패\), 1\(오류 발생\), 2\(성공적으로 업그레이드됨\) \(실패 후 스크립트를 재시도할 때 &quot;fmUpgradeStatus&quot; &lt;= processLevel인 파일만 다시 처리되고 그렇지 않으면 무시됩니다. 기본값은 1입니다.\)
    - &#39;ignoreImageVersions&#39;: true/false \(이미지 버전 처리를 무시합니다. 기본값은 false입니다.\)
    
    >[!NOTE]
    >
    > 폴더 수준 또는 전체 콘텐츠/dam 또는 동일한 폴더에서 콘텐츠 마이그레이션을 실행할 수 있습니다 \(마이그레이션 다시 실행\).

1. 서버가 성공적으로 마이그레이션되면 다음 워크플로우 및 사후 처리가 서버에서 계속 작업할 수 있습니다.

   - **DAM 자산 업데이트** 워크플로우
   - **DAM 메타데이터** 워크플로우

>[!NOTE]
>
> 일부 파일이 처리되지 않았거나 마이그레이션 전에 손상된 경우 마이그레이션 후에도 손상된 상태로 유지됩니다.
