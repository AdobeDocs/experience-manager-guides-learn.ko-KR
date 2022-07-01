---
title: 추가 방법 [!DNL AEM Guides] 아래와 같이 [!DNL AEM as a Cloud Service] 환경
description: 추가 방법 알아보기 [!DNL AEM Guides] 아래와 같이 [!DNL AEM as a Cloud Service] 환경
exl-id: a1e020c2-360c-4d71-b5fd-8179d9ceacda
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# [!DNL AEM Guides] as a Cloud Service 배포

추가 방법 알아보기 [!DNL Guides] 아래와 같이 [!DNL AEM as a Cloud Service] 환경.

## Cloud Manager Git 파이프라인을 통한 수동 배포

구입한 경우 [!DNL AEM Guides] 2022년 3월 29일 이전에 as a Cloud Service으로 제공되는 이 배포 지침을 따르십시오.

* 새로 시작하는 경우 [!UICONTROL Cloud Manager] XML 플러그인이 이미 통합된 아래 보고서의 코드를 사용하여 다음을 수행합니다. https://github.com/Adobe-TCS/XML-documentation-for-AEMaaCS

* 에서 이미 사용자 지정 항목을 체크 인한 경우 [!UICONTROL Cloud Manager] git repo 아래의 보고서를 참조하여 기존 코드에 XML 플러그인을 추가하는 방법에 대한 지침을 확인할 수 있습니다. https://github.com/Adobe-TCS/DoX-Installer-for-AEMaaCS

## Cloud Manager를 통한 배포

구입한 고객인 경우 [!DNL AEM Guides] 03/29/2022 또는 그 후에 as a Cloud Service을 사용하여 다음 지침을 따라 [!DNL Guides] 아래와 같이 [!DNL AEM as a Cloud Service] 환경:

1. 에 로그인합니다. [!UICONTROL Cloud Manager].

1. 구성할 프로그램 편집 [!DNL AEM Guides].

1. 다음으로 전환 **[!UICONTROL 솔루션 및 추가 기능]** 탭.

1. 에서 **[!UICONTROL 솔루션 및 추가 기능]** 테이블 **[!UICONTROL 자산]**.

1. 선택 **[!UICONTROL 안내서]** 을(를) 선택합니다. **[!UICONTROL 저장]**.

AEM 안내서 솔루션의 자동 프로비저닝을 위해 프로그램을 구성했습니다.

![AEM 안내서 솔루션 구성](assets/addon-configuration.png)

>[!NOTE]
>
>설치하려면 [!DNL AEM Guides] 통합 프로그램의 모든 환경에서 환경과 연관된 파이프라인을 실행해야 합니다. 설치하기 위해 CM Git 코드 베이스에 추가 구성이 필요하지 않습니다 [!DNL AEM Guides].
