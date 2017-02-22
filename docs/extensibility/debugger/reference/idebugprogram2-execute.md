---
title: "IDebugProgram2::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Execute"
helpviewer_keywords: 
  - "IDebugProgram2::Execute"
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

继续运行从一种停止状态的此过程。  \(例如步骤\) 清除所有以前执行状态和程序再次开始执行。  
  
> [!NOTE]
>  此方法已被否决。  请改用 [执行](../../../extensibility/debugger/reference/idebugprocess3-execute.md) 方法。  
  
## 语法  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```c#  
int Execute();  
```  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 当用户开始执行从其他某个程序的线程中的一种停止状态，此方法调用此过程。  ，当用户选择 **开始** 命令在 IDE 时，的 **调试** 菜单此方法被调用。  此方法的实现可能十分简单调用当前线程的 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 方法在程序。  
  
> [!WARNING]
>  不要将一个终止的事件或一个即时 \(\) 同步事件。 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ，当处理此时调用，否则调试器会停止。  
  
## 请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)