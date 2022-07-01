---
title: 주제 내의 단락을 번역에서 제외
description: 주제 내의 단락을 번역에서 제외하는 방법
feature: Translation
role: User
exl-id: 21e41bb4-52f3-4352-92d9-4a60f636de99
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# 주제 내의 단락을 번역에서 제외하는 방법

가장 쉬운 방법은 translation=no 특성을 사용하는 것입니다.

+ 작성자는 추가 속성을 **translation=no** 번역하지 않을 단락의 경우. 번역 공급업체에게 정보를 제공해야 하며, 이 특성을 사용하여 텍스트를 무시하기 위해 끝에 구성을 수행할 수 있습니다.
+ OOTB 기계 번역(평가판 Microsoft 번역 커넥터 사용)은 동일한 동작을 나타냅니다.
+ Microsoft 번역 테스트 : 정의한 경우 **translate=no** 단락 수준의 속성을 지정하면 전체 단락이 번역되지 않습니다. 이 속성은 어떤 요소에서든 정의할 수 있으며 해당 요소 내의 컨텐츠는 번역되지 않습니다.


다음은 이를 자세히 설명하는 몇 가지 스크린샷입니다.

**소스 컨텐츠**

![소스 컨텐츠](assets/source-content.jpg)

**번역된 스페인어 콘텐츠**

![번역된 스페인어 콘텐츠](assets/trans-content.jpg)
