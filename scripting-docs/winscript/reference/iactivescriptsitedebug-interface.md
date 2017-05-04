---
title: "IActiveScriptSiteDebug 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebug 接口"
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug 接口
智能宿主实现 `IActiveScriptSiteDebug` 接口执行文件管理和参与调试。  `IActiveScriptSite` 对象通常提供 `IActiveScriptSiteDebug` 接口的实现。  如果这样做，请调用 `IActiveScriptSite::QueryInterface` 方法获取 `IActiveScriptSiteDebug` 接口。  
  
 除了从 `IUnknown` 继承的方法之外，`IActiveScriptSiteDebug` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|用于使语言引擎委托 `IDebugCodeContext::GetSourceContext`。|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|返回调试应用程序对象与此脚本站点。|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|获取下脚本应添加的应用程序节点。|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|如何允许一个智能宿主确定处理运行时错误。|