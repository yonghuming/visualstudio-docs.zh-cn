---
title: "IDebugProgramHost2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramHost2"
helpviewer_keywords: 
  - "IDebugProgramHost2 接口"
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramHost2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口提供有关程序的宿主 \(过程\) 信息。  
  
## 语法  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎实现位于所提供有关承载的信息的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口处理对象的此接口。  这是一个可选接口。  
  
## 调用方的说明  
 调用 `IDebugProgram2` 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugProgramHost2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|获取标题，友好名称，或者承载的文件名处理此过程。|  
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|获取承载的进程标识符处理此过程。|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|获取宿主进程此过程运行的计算机的名称。|  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)