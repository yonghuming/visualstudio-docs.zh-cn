---
title: "IActiveScriptSiteWindow::EnableModeless | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.EnableModeless
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_EnableModeless"
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow::EnableModeless
使宿主启用或禁用其主窗口以及任何无模式对话框。  
  
## 语法  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### 参数  
 `fEnable`  
 \[in\]中标记，因此，如果 `TRUE`，启用主窗口和无模式对话框，或者，如果 `FALSE`，禁用它们。  
  
## 返回值  
 返回 `S_OK`，如果成功或 `E_FAIL`，如果错误。  
  
## 备注  
 此方法与 `IOleInPlaceFrame::EnableModeless` 方法相同。  
  
 调用此方法可以嵌套。  
  
## 请参阅  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)