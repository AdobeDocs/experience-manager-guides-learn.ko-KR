---
title: DITA-OT를 사용하여 메타데이터를 출력에 전달합니다
description: DITA-OT를 사용하여 메타데이터를 출력에 전달하는 방법을 알아봅니다
exl-id: 637895e5-aece-4827-a32e-f2ae3e3704ef
source-git-commit: c74badebbcb4733fb9caa79c646b1d1e5c8bfe8e
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# DITA-OT를 사용하여 메타데이터를 출력에 전달합니다 {#id21BJ00QD0XA}

메타데이터는 출력에 대한 추가 정보입니다. AEM 안내서에서는 기존 메타데이터를 전달하거나 사용자 지정 메타데이터 태그를 만들 수 있습니다. DITA-OT 게시를 사용하여 AEM, PDF, HTML5, EPUB 및 사용자 지정 형식 출력에 메타데이터를 전달할 수 있습니다.

DITA-OT 게시를 사용하여 메타데이터를 출력에 전달하려면 다음 단계를 수행하십시오.

1. 에서 **자산 UI**&#x200B;로 이동하고 DITA-OT에 메타데이터를 전달할 DITA 맵 파일을 클릭합니다.
1. 메타데이터 필드를 전달할 출력 사전 설정을 선택하고 편집합니다. 예를 들어, PDF 출력 사전 설정을 선택합니다.
1. 선택 **DITA-OT** 생성 &lt;output> 선택한 출력 사전 설정에서 옵션을 사용합니다.

   ![](images/custom-meta-data-output-preset.png){width="800" align="left"}

1. 속성 드롭다운에서 DITA-OT 게시에 전달할 메타데이터를 선택합니다.

   속성 드롭다운에 사용자 지정 속성과 기본 속성이 모두 나열됩니다. 예를 들어 위의 스크린샷 작성자는 사용자 지정 속성이며 `dc:description`, `dc:language`, `dc:title`, 및 `docstate` 는 기본 속성입니다.

   >[!NOTE]
   >
   > 이러한 속성은 다음 위치에서 사용할 수 있는 metadataList 파일에서 선택됩니다.`/libs/fmdita/config/metadataList`. 기본적으로 이 파일에는 네 개의 속성이 나열되어 있습니다. `dc:description`, `dc:language`, `dc:title`, 및 `docstate`.

   이 파일은 다음 위치에서 오버레이할 수 있습니다. `/apps/fmdita/config/metadataList`.

   값을 이미 정의한 사용자 지정 속성을 전달하려면 를 참조하십시오 [DITA-OT PDF 출력에서 AEM 메타데이터 사용](https://experienceleaguecommunities.adobe.com/t5/xml-documentation-discussions/use-aem-metadata-in-dita-ot-pdf-output/td-p/411880).

1. 에서 **속성** 드롭다운에서 필요한 사용자 지정 및 기본 속성을 선택합니다. 예를 들어, `author`, `dc:title`, 및 `dc:description`. 이것이 표준입니다 `metadata/properties` 파일을 만들면 생성됩니다. 선택한 속성이 드롭다운 상자 아래에 나열됩니다.

   ![](images/selected-metadata-properties.png){width="300" align="left"}

1. 클릭 **완료** 왼쪽 상단에서 변경 사항을 저장합니다.
1. 출력을 생성합니다.

선택한 메타데이터 속성이 DITA-OT를 사용하여 생성된 출력에 전달됩니다.

**상위 항목:**[&#x200B;출력 생성](generate-output.md)
