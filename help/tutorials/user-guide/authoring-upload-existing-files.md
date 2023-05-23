---
title: 파일 업로드
description: 파일 업로드 방법 알아보기
exl-id: d6a73953-94dd-4fa5-b09c-5e4c77fead62
source-git-commit: 8073716bccacbe8d6a158b44d5106b083e3a5dcd
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# 파일 업로드 {#id176FF000JUI}

AEM Guides에 사용할 기존 DITA 콘텐츠 저장소가 있을 가능성이 높습니다. 이러한 기존 콘텐츠의 경우 다음 접근 방식 중 하나를 사용하여 콘텐츠를 AEM 저장소에 일괄 업로드할 수 있습니다.

>[!IMPORTANT]
>
> 다음을 참조하십시오 [Adobe Experience Manager as a Cloud Service Assets에 디지털 자산 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html) 자세한 내용은 AEM에서 지원되는 콘텐츠 업로드 방법을 참조하십시오.

## 자산 콘솔 사용자 인터페이스

데스크탑에서 컨텐츠를 선택하고 AEM 사용자 인터페이스 \(웹 브라우저\)를 대상 폴더로 드래그할 수 있습니다. 자세한 내용은 [에셋 업로드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html#upload-assets) AEM 설명서에서 참조할 수 있습니다.

## AEM 데스크탑 앱

크리에이티브 전문가이고 로컬 데스크탑의 에셋을 관리하려는 경우 AEM 데스크탑 앱을 사용하십시오. 데스크탑 애플리케이션을 사용하여 이러한 에셋을 열고 편집할 수 있습니다. 버전을 유지 관리하고 다른 사용자와 파일을 공유할 수도 있습니다. 자세한 내용은 [AEM 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html).

## 일괄 에셋 수집기

대규모 마이그레이션 및 경우에 따라 일괄 수집이 있는 경우 일괄 에셋 수집기 를 사용하여 콘텐츠를 업로드하십시오. 이 도구를 사용하면 Azure 또는 S3와 같이 지원되는 데이터 저장소에서 대량 콘텐츠를 업로드할 수 있습니다. 자세한 내용은 [일괄 에셋 수집기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html?lang=en#asset-bulk-ingestor).

## 일괄 업로드에 FrameMaker 사용

Adobe FrameMaker에는 기존 DITA 및 기타 FrameMaker 문서를 쉽게 업로드할 수 있는 강력한 AEM 커넥터가 포함되어 있습니다.`.book` 및 `.fm`\) 을 AEM에 추가합니다. 단일 파일 업로드, 종속성 유무에 관계없이 전체 폴더 업로드 \(예: 콘텐츠 참조, 상호 참조 및 그래픽\)와 같은 다양한 파일 업로드 기능을 사용할 수 있습니다.

FrameMaker에서 일괄 업로드 기능을 사용하는 방법에 대한 자세한 내용은 섹션을 참조하십시오 *CRX 폴더를 만들고 파일 업로드* ( FrameMaker 사용 안내서)를 참조하십시오.

## 콘텐츠 업로드 중 오류 처리 {#id201MI0I04Y4}

하나 이상의 파일을 업로드하지 못한 경우 업로드 프로세스가 끝날 때 업로드에 실패한 파일 목록과 함께 프롬프트가 표시됩니다.

![](images/uuid-files-failed-to-upload_cs.png){width="650" align="center"}

다양한 파일 업로드 시나리오에 대한 자세한 내용은 을 참조하십시오. [DITA 컨텐트 업로드](authoring-file-management.md#).

AEM 데스크탑 앱이나 자산 대량 수집기와 같은 도구를 사용하는 경우 중복 파일에서 수행할 작업은 AEM 서버의 설정에 의해 제어됩니다. 이 구성에 대해 알아보려면 시스템 관리자에게 문의하십시오.

**상위 항목:**[&#x200B;콘텐츠 관리](authoring.md)