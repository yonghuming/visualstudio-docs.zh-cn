---
title: "IDebugProgramDestroyEventFlags2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgramDestroyEventFlags2 接口"
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

，在调试会话结束时，可以调试引擎重写 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 的默认行为。  
  
## 语法  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## 实现者说明  
 此接口实现调试引擎。  为可能创建和销毁在进程的生存期内的多个程序的宿主是有用的。  
  
## 方法  
 下表显示 `IDebugProgramDestroyEventFlags2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|检索程序销毁标志。|  
  
## 备注  
 ，在任何过程发送了一个程序销毁事件后， [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 的默认行为是返回设计模式。  此接口可以调试引擎更改此行为。  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll