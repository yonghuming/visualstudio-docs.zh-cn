---
title: "IDebugMemoryContext2 | Microsoft Docs"
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
  - "IDebugMemoryContext2"
helpviewer_keywords: 
  - "IDebugMemoryContext2 接口"
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示在运行程序的计算机的地址空间中的位置进行调试。  
  
## 语法  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口表示在内存中的地址。  
  
## 调用方的说明  
 为 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) 或 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) 的调用返回此接口。  此外，调用 [添加](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) ，并 [减](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) 返回此接口的新副本，在应用后适当的算术运算。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugMemoryContext2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|获取用户可显示的名称此上下文中。|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|获取描述此上下文的信息。|  
|[添加](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|添加指定值到当前上下文的地址创建新的上下文。|  
|[减](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|从当前上下文的地址减去指定值创建新的上下文。|  
|[比较](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|比较两个上下文以指示的方式比较标志。|  
  
## 备注  
 visual studio 的 **内存** 窗口调用 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) 获取包含用于内存地址的该计算表达式的 `IDebugMemoryContext2` 接口。  此上下文随后传递给 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) 和 [WriteAt](../Topic/IDebugMemoryBytes2::WriteAt.md) 指定该地址读取或写入。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../Topic/IDebugMemoryBytes2::WriteAt.md)