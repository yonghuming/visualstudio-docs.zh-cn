---
title: "IDebugStackFrame2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2"
helpviewer_keywords: 
  - "IDebugStackFrame2 接口"
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示在某个调用堆栈的一个堆栈帧在特定线程上。  
  
## 语法  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口表示堆栈帧。  
  
## 调用方的说明  
 调用 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 检索 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 接口。  调用 [下一步](../Topic/IEnumDebugFrameInfo2::Next.md) 检索包含 `IDebugStackFrame2` 接口的 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 结构。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugStackFrame2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|获取堆栈帧的代码上下文。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|获取堆栈帧的文档上下文。|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|获取堆栈帧的名称。|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|获取堆栈帧的说明。|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|获取物理地址范围的计算机相关的表示形式与堆栈帧。|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|获取用于执行的表达式计算一次计算上下文堆栈帧和线程的当前上下文中。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|获取该语言与堆栈帧。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|获取特性的声明与堆栈帧。|  
|[EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)|创建堆栈帧属性的枚举数。|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|获取线程与堆栈帧。|  
  
## 备注  
 此接口来获得，仅当正在调试的程序终止了在断点上时 \(生成由用户设置的断点或异常\)。  从该接口，表达式上下文可以获取计算表达式，注册该列表可返回，或者调用堆栈来获取、选中。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)