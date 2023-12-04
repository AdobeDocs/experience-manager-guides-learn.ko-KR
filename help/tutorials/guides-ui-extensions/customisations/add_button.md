---
sidebar_position: 1
source-git-commit: 42052b37724f97e34ab007db4cc3d9f9524ad3a2
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# 간단한 사용자 정의 예

이제 AEM Guides 앱에서 이러한 사용자 지정 사항을 통합하는 방법을 살펴보겠습니다.

예를 들어, 앱의 기존 보기에서 이 단추를 추가하려고 합니다.
이를 위해 다음과 같은 3가지 기본 사항이 필요합니다.

1. 다음 `id` 구성 요소를 추가하려는 JSON 보기.
2. 다음 `target`, 즉 새 구성 요소를 추가하려는 JSON의 위치입니다. 다음 `target` 다음을 사용하여 정의됨: `key` 및 `value`. 키-값 쌍은 구성 요소를 고유하게 식별하는 데 도움이 되는 구성 요소를 정의하는 데 사용되는 모든 속성일 수 있습니다.
색인을 사용하여 타겟을 참조할 수도 있습니다.
3개의 viewStates가 있습니다.  `APPEND`, `PREPEND`, `REPLACE`.
3. 새로 생성된 구성 요소 및 해당 메서드의 JSON입니다.

검토에 사용된 주석 도구 상자에 버튼을 추가하여 AEM에서 파일을 열려고 합니다.

```typescript
export default {
  id: 'annotation_toolbox', 
  view: {
    items: [
      {
        component: 'button',
        icon: 'linkOut',
        title: 'Open topic in Assets view',
        'on-click': 'openTopicInAEM',
        target: {
          key: 'value',
          value: 'addcomment',
          viewState: VIEW_STATE.APPEND

        },
      },
    ],
  },
  controller: {
    openTopicInAEM: function (args) {
        const topicIndex = tcx.model.getValue(tcx.model.KEYS.REVIEW_CURR_TOPIC)
        const {allTopics = {}} = tcx.model.getValue(tcx.model.KEYS.REVIEW_DATA) || {}
        tcx.appGet('util').openInAEM(allTopics[topicIndex])
    },
  },
}
```

위의 예에는 다음이 있습니다.

1. 다음 `id` 구성 요소를 삽입하려는 JSON의 경우 `annotation_toolbox`
2. 대상은 입니다. `addcomment` 단추를 클릭합니다. 단추 다음에 추가 `addcomment` viewState를 사용하는 단추 `append`.
3. 우리는 컨트롤러에서 버튼의 온-클릭 이벤트를 정의합니다.

에 대한 JSON [`annotation_toolbox`](./../../../jsons/review_app/annotation_toolbox.json)

사용자 지정 전에 주석 도구 상자는 다음과 같이 표시되었습니다.

![주석 도구 상자](imgs/annotation_toolbox.png "주석 도구 상자")

사용자 지정 후 주석 도구 상자는 다음과 같습니다.

![사용자 지정 주석 도구 상자](imgs/customised_annotation_toolbox.png "사용자 지정된 주석 도구 상자")

## CSS 추가

일관성을 위해 이미 스타일이 지정된 구성 요소를 제공합니다. 삽입된 JSON에는 고유 스타일이 적용됩니다. css를 관리하는 기본 방법은 확장의 extraClass 키를 통하는 것입니다.

```js
{    
    "view":{
        items:[
            {
                compoenent:"button",
                extraClass:"underline bg-red",
            }
        ]
    }
}
```

css 파일을에 추가하여 CSS 클래스와 함께 사용자 정의 스타일을 지정할 수 있습니다. [clientlibs](#clientlibs). 빌드하는 동안 [배풍](https://tailwindcss.com/docs/utility-first) tailwind의 유틸리티 클래스에 대한 출력입니다. 다음에 대한 구성을 찾을 수 있습니다. [tailwind.config.js](../../../tailwind.config.js)