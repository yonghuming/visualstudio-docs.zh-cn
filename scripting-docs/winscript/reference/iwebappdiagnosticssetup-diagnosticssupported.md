---
title: "IWebAppDiagnosticsSetup::DiagnosticsSupported | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::DiagnosticsSupported"
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::DiagnosticsSupported
确定诊断是否位于应用程序的支持。  如果 [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) 调用了实现具有非null值的对象此接口，[DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) 返回 `true`。  否则，它将返回 `false` 并调用 [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) 失败。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup 接口](../../winscript/reference/iwebappdiagnosticssetup-interface.md) 由PDM v11.0实现和更大。  找到在activdbg100。  
  
## 语法  
  
```cpp  
HRESULT DiagnosticsSupported(  
        [out, retval] VARIANT_BOOL* pRetVal  
        );  
```  
  
#### 参数  
 `pRetVal`  
 如果 [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) 调用了实现具有非null值的对象此接口，[DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) 返回 `true`。  否则，它将返回 `false`，并调用 [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) 失败。