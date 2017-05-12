---
title: "IWebAppDiagnosticsSetup 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup 接口"
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IWebAppDiagnosticsSetup 接口
此接口由PDM正在调试的进程实现调试应用程序创建COM对象和启用web诊断。  如果PDM调试应用程序对象实现 [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438)，Internet Explorer在引用 [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449) [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) 调用此一旦创建，并传递。  WWA应用程序在WWA接口IWebApplicationHost调用 [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) 并传递。  如果 [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) 调用使用非null值，[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) 返回true。  否则，它将返回错误并调用 [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) 失败。  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` 由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 方法  
 此接口公开下列方法。  
  
|方法|说明|  
|--------|--------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|获取文本文档所指定的筛选器隐藏。|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|确定指定的文档是否属于某一个此节点的子节点。|