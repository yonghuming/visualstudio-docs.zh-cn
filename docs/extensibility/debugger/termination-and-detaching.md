---
title: "终止和分离 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程序、 沧 ゎ ㄆ ン"
  - "调试引擎，与程序分离"
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 终止和分离
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下面描述正常终止。  
  
## 讨论  
 在 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 或 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 后继续，接口，如果没有断点、异常、运行时错误或无限循环访问应用程序进行调试，正在调试的程序将已完成运行。  这是正常终止。  
  
 您必须发送 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 到实现正常终止。  这需要执行 [IDebugProgramDestroyEvent2:: GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md) 方法。  
  
## 请参阅  
 [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)