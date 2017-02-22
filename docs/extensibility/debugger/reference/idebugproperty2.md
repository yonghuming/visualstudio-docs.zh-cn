---
title: "IDebugProperty2 | Microsoft Docs"
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
  - "IDebugProperty2"
helpviewer_keywords: 
  - "IDebugProperty2 接口"
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示堆栈帧属性，程序文档属性，或某个其他属性。  属性通常是表达式计算的结果。  
  
> [!NOTE]
>  不应与该含义混淆为 “属性”使用此类的成员变量，不过， `IDebugProperty2` 可以表示这些实体。  
  
## 语法  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 表示特定种类的此接口值。  例如，由于表达式计算、用于显示内存使用的内存上下文或注册及其值，列出该值可以是数值。  
  
## 调用方的说明  
 调用 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 获取此接口，表示计算的结果。  `IDebugExpression2::EvaluateAsync` 通过发送 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 接口返回此接口添加到 SDM，然后调用 [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) 检索属性。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) 返回此接口提供该关联的脚本文档。  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) 返回此接口表示函数的返回值。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) 返回此接口表示程序的各个属性 \(如名称或内存上下文。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 返回此接口表示堆栈帧的各个属性 \(例如本地变量。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugProperty2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|填充描述一个属性的一 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 结构。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|设置属性的值从字符串的。|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|设置属性的值从给定的值的引用。|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|枚举属性的子级。|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|返回属性的父级。|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|返回描述属性的首选派生属性的属性。|  
|[GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md)|返回由属性值组成的内存中字节数组。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|返回属性值的内存上下文。|  
|[GetSize](../Topic/IDebugProperty2::GetSize.md)|返回的大小，以字节为单位\)，属性值。|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|返回对该属性。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|返回属性的扩展的信息。|  
  
## 备注  
 一个属性，如由 `IDebugProperty2` 接口，可视为与名称、类型和地址的值。  使用泛称， `IDebugProperty2` 无法在父和子节点表示具有一个层次结构中的任何，。  
  
 例如属性通常是瞬间完成的，最后，仅在当前堆栈帧，。  另一方面，，只要该值在内存中，保持引用，如由 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 接口，继续。  
  
 IDE 会使用 `IDebugProperty2` 接口允许用户浏览和修改属性在运行时。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)