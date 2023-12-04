---
sidebar_position: 2
source-git-commit: 42052b37724f97e34ab007db4cc3d9f9524ad3a2
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---


# 컨텍스트 메뉴 사용자 정의

다음 컨텍스트 메뉴를 사용자 지정할 수 있습니다.

- `file_options`
컨트롤러:
   - 맵 보기: `ditamap_viewer_controller`
   - 저장소 패널: `repository_panel_controller`
   - 즐겨찾기 패널: `collection_tree_controller`
   - 파일 속성 참조 링크: `file_references_links_controller`
   - 저장소 검색 패널: `repository_search_controller`
   - 제목 구성표 패널: `subject_scheme_tree_controller`

- `folder_options`
컨트롤러:
   - 저장소 패널: `repository_panel_controller`
   - 즐겨찾기 패널: `collection_tree_controller`

- `collection_options`
컨트롤러:
   - 즐겨찾기 패널: `collection_tree_controller`

- `map_view_options`
컨트롤러:
   - 맵 보기: `ditamap_viewer_controller`

- `baseline_panel_menu`
컨트롤러:
   - 기준선 패널: `baseline_panel`

- `preset_item_menu`
컨트롤러:
   - 사전 설정 패널: `preset_panel`

새 고유 ID를 정의하여 상황에 맞는 메뉴를 만들 수도 있습니다.

이제 각 컨텍스트 메뉴에는 `controller id` 와 연관되어 있습니다. 이 컨트롤러는 `on-event` 다양한 상황에 맞는 메뉴 옵션 기능

예를 들어 이해할 수 있도록 합니다.

```js title=customise_context_menu.js"
const fileOptions = {
    id: "file_options",
    contextMenuWidget: "repository_panel",
    view: {
            items: [
                {
                    component: "div",
                    target: {
                        key:"displayName",value: "Delete",                    
                        viewState: VIEW_STATE.REPLACE
                    }
                },
                {
                    component: "div",
                    target: {
                        key:"displayName",value: "Edit",                    
                        viewState: VIEW_STATE.REPLACE
                    }
                },
                {
                    "displayName": "Download",
                    "data": {
                      "eventid": "downloadFile"
                    },
                    "icon": "downloadFromCloud",
                    "class": "menu-separator",         
                    target: {
                        key:"displayName",value: "Duplicate",                    
                        viewState: VIEW_STATE.REPLACE
                    }
                },
            ]

    },

    controller: {
        downloadFile(){
            const path  = this.model.selectedItem.path
            this.loader.loadDitaFile(path).then((file) => {
              function download_file(name, contents) {
                const mime_type = "text/plain";
        
                const blob = new Blob([contents], {type: mime_type});
        
                const dlink = document.createElement('a');
                dlink.download = name;
                dlink.href = window.URL.createObjectURL(blob);
                dlink.onclick = function() {
                    // revokeObjectURL needs a delay to work properly
                    const that = this;
                    setTimeout(function() {
                        window.URL.revokeObjectURL(that.href);
                    }, 1500);
                };
        
                dlink.click();
                dlink.remove();
            }
            download_file(path,file.xml)
            });
          }
    }
}
```

이제 이 코드가 수행하는 작업을 이해하겠습니다.

1. `id` 는 사용자 지정할 컨텍스트 메뉴를 식별하는 데 사용됩니다.
2. `contextMenuWidget` 을(를) 정의하는 데 사용됩니다. `widget id` 또는 `component` 컨텍스트 메뉴를 호출하고 `events`.

나머지 부분은 동일하게 유지되며, `view` 항목을 정의하는 데 사용됩니다. `target` 는 옵션과 를 대체, 추가 또는 추가할 위치를 나타냅니다. `contextMenuWidget` 컨트롤러가 다음을 처리합니다. `on-click` 이벤트.