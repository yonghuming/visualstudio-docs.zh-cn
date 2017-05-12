---
title: "IWebAppDiagnosticsObjectInitialization 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization 接口"
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsObjectInitialization 接口
此接口在实现 [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)的选件类中实现。  [IWebAppDiagnosticsSetup 接口](../../winscript/reference/iwebappdiagnosticssetup-interface.md) 由对象实现 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)。  在许多情况下此对象是PDM。  
  
 在对象中创建后，[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) 调用与PDM的引用调试应用程序和 `CreateObjectWithSiteAtWebApp`的 `hPassToObject` 参数。  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization` 在activdbg100.h.中。  
  
## 方法  
 此接口公开下列方法。  
  
|方法|说明|  
|--------|--------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|初始化对象。|