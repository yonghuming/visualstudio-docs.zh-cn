---
title: "在中断模式中单步执行 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "中断模式下，单步执行"
  - "单步执行，在中断模式下"
  - "调试 [调试 SDK]，在中断模式下单步执行"
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 在中断模式中单步执行
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下面描述发生的处理，调试器处于中断模式，并且必须逐句通过代码:  
  
## 单步执行处理  
  
1.  调用带有 [STEPKIND](../../extensibility/debugger/reference/stepkind.md) 和 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) 参数的 [IDebugProgram2:: 步骤](../../extensibility/debugger/reference/idebugprogram2-step.md) 执行中的步骤。  
  
2.  当该步骤完成时，请发送 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 作为一个停止点的事件。  
  
## 请参阅  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)