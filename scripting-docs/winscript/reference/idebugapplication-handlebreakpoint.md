---
title: "IDebugApplication::HandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleBreakPoint"
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleBreakPoint
使当前线程阻塞并将断点的通知给调试器IDE。  
  
## 语法  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### 参数  
 `br`  
 \[in\]中断的原因。  
  
 `pbra`  
 \[in\]执行的操作，当调试器还原应用程序。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 语言引擎调用此方法在命中断点的线程中。  此方法会阻止当前线程并将断点通知给调试器IDE。  当调试器还原应用程序时，`pbra` 参数指定使用哪些操作。  
  
> [!NOTE]
>  在断点期间，语言引擎可以由线程调用执行任务\(如枚举堆栈帧或计算表达式。  
  
 此方法使 `IApplicationDebugger::onHandleBreakPoint` 调用。  
  
## 请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON 枚举](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION 枚举](../../winscript/reference/breakresumeaction-enumeration.md)