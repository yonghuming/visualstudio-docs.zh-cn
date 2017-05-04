---
title: "IDebugApplication::HandleRuntimeError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleRuntimeError
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleRuntimeError"
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleRuntimeError
使当前线程阻塞并将该错误的通知给调试器IDE。  
  
## 语法  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### 参数  
 `pErrorDebug`  
 \[in\]发生的错误。  
  
 `pScriptSite`  
 \[in\]线程的脚本站点。  
  
 `pbra`  
 \[in\]执行的操作，当调试器还原应用程序。  
  
 `perra`  
 \[in\]执行的操作，当调试器还原应用程序，则出现错误。  
  
 `pfCallOnScriptError`  
 \[out\]为 `TRUE` 的标志，如果引擎应调用 `IActiveScriptSite::OnScriptError` 方法。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 语言引擎调用此方法在导致运行时错误的线程中。  此方法使当前线程块并发送要发送的错误通知给调试器IDE。  当调试器IDE还原应用程序时，此方法返回与要执行的操作。  
  
> [!NOTE]
>  在运行时错误，语言引擎可以由线程调用执行此类任务与枚举堆栈帧或计算表达式时。  
  
## 请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug 接口](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION 枚举](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 枚举](../../winscript/reference/errorresumeaction-enumeration.md)