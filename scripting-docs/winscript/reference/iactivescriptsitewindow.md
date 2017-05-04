---
title: "IActiveScriptSiteWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteWindow 接口"
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow
此接口由支持在对象的用户界面和 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 相同的宿主实现。  不支持一个用户界面，如服务器的主机，而不实现 `IActiveScriptSiteWindow` 接口。  脚本引擎访问此接口通过调用从 `IActiveScriptSite`的 `QueryInterface`。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|检索可能以弹出窗口所有者脚本引擎必须公开的窗口句柄。|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|使宿主启用或禁用其主窗口以及任何无模式对话框。|  
  
## 请参阅  
 [活动脚本接口](../../winscript/reference/active-script-interfaces.md)