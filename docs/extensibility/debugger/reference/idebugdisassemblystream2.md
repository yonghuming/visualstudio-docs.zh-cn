---
title: "IDebugDisassemblyStream2 | Microsoft Docs"
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
  - "IDebugDisassemblyStream2"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2 接口"
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示指令流。  
  
## 语法  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎实现此接口支持代码中反汇编。  
  
## 调用方的说明  
 为 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 方法的调用返回此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugDisassemblyStream2`方法。  
  
|方法|说明|  
|--------|--------|  
|[读取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|从 " 反汇编流的当前位置开始阅读说明。|  
|[查找](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|将反汇编流中读取的指针命令的许多相对一个指定的位置。|  
|[GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)|返回特定代码上下文的代码位置标识符。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|返回代码上下文对象具有指定的代码位置标识符相对应。|  
|[GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)|返回表示当前代码位置的代码位置标识符。|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|获取源文档与此反汇编流。|  
|[GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)|获取此范围反汇编流。|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|获取反汇编流的大小。|  
  
## 备注  
 反汇编流可以创建表示整个地址空间或函数或模块该空间中。  每个指令通过对 [读取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 方法的调用返回的 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 结构表示。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)