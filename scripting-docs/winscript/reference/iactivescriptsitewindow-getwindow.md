---
title: "IActiveScriptSiteWindow::GetWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.GetWindow
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_GetWindow"
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteWindow::GetWindow
检索句柄可能以弹出窗口所有者脚本引擎必须显示的窗口。  
  
## 语法  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### 参数  
 `phwnd`  
 \[in\]接收窗口句柄变量的地址。  
  
## 返回值  
 返回 `S_OK`，如果成功或 `E_FAIL`，如果错误。  
  
## 备注  
 此方法类似于 `IOleWindow::GetWindow` 方法。  
  
## 请参阅  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)