---
title: "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp"
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
此方法用于共同创建使用 `dwClsContext`，ID通过使用 `rclsid` 的选件类。  这类似于 [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) 的工作方式，不同之处在于，在 `CreateObjectWithSiteAtWebApp` 对象在Web应用程序的用户界面线程创建异步。  选件类ID指定的对象应实现 [IWebAppDiagnosticsObjectInitialization 接口](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)。  在对象中创建后，[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) 调用与PDM的引用调试应用程序和 `CreateObjectWithSiteAtWebApp`的 `hPassToObject` 参数。  可以使用此方法将传递给app句柄已复制 [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450)的匿名管道。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup 接口](../../winscript/reference/iwebappdiagnosticssetup-interface.md) 由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(  
        [in] REFCLSID rclsid,   
        [in] DWORD dwClsContext,   
        [in] REFIID riid,   
        [in] DWORD_PTR hPassToObject  
        );  
  
```  
  
#### 参数  
 `rclsid`  
 创建的选件类的选件类ID。  
  
 `dwClsContext`  
 代码将运行的上下文。  在许多情况下为CLSCTX\_INPROC\_SERVER。  
  
 `riid`  
 未使用。  
  
 `hPassToObject`  
 一次将对象传递给它的值在UI线程上创建，因此，如果对象实现 [IWebAppDiagnosticsObjectInitialization 接口](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)。