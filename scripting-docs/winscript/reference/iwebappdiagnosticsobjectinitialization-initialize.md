---
title: "IWebAppDiagnosticsObjectInitialization::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization::Initialize"
ms.assetid: 7ccfac28-9f65-4e1c-a0fb-a8a6c7f75b63
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IWebAppDiagnosticsObjectInitialization::Initialize
初始化使用 [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)创建的对象。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsObjectInitialization 接口](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md) 在activdbg100.h.中。  
  
## 语法  
  
```cpp  
HRESULT Initialize(  
        [in, annotation("__in")] HANDLE_PTR hPassedHandle,  
        [in, annotation("__in")] IUnknown* pDebugApplication  
        );  
```  
  
#### 参数  
 `hPassedHandle`  
 通过在 `hPassToObject` 参数的 [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) 方法的句柄。  
  
 `pDebugApplication`  
 对象创建的PDM应用程序。