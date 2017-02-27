---
title: "IDebugReference2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2"
helpviewer_keywords: 
  - "IDebugReference2 接口"
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugReference2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示对堆栈帧属性或某个其他属性。  
  
> [!NOTE]
>  `IDebugReference2` 保留以后使用，并且，其所有方法应返回 `E_NOTIMPL`。  
  
## 语法  
  
```  
IDebugReference2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 表示引用的此接口来特定类型的值。  例如，由于表达式计算、用于显示内存使用的内存上下文或注册及其值，列出该值可以是数值。  
  
## 调用方的说明  
 调用 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) 获取此接口。  [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) 和 [GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md) 还返回此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugReference2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|获取描述此引用的 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 结构。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|将此的值从字符串。|  
|[SetValueAsReference](../Topic/IDebugReference2::SetValueAsReference.md)|将此的值从另一个引用引用。|  
|[EnumChildren](../Topic/IDebugReference2::EnumChildren.md)|此枚举的子级引用。|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|获取此的父引用。|  
|[GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md)|获取当前派生引用此引用。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|获取此引用引用的内存中字节数组。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|获取此的一个内存上下文引用。|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|获取范围，在字节，此引用。|  
|[SetReferenceType](../Topic/IDebugReference2::SetReferenceType.md)|将此引用类型。|  
|[比较](../../../extensibility/debugger/reference/idebugreference2-compare.md)|比较此引用与另一个。|  
  
## 备注  
  
> [!NOTE]
>  不应与该含义混淆为 “属性”使用此类的成员变量，不过， `IDebugReference2` 可以表示这些实体。  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 通常表示属性，，而 `IDebugReference2` 表示对属性，对正在调试的程序的对象。  
  
 属性和引用之间的主要差异在于属性指的是命名实例，则，而引用所引用未命名的实例。  例如，属性可以由 `"a.b"`指程序堆上的对象。  另一个属性可以引用对象和 `"c.d"`相同。  引用此属性模式要求该 `"a.b"` 或 `"c.d"` 在范围内。  此相同的对象的引用是无名称的;，只要该对象的内存有效，对象可以引用。  
  
 一 `IDebugProperty2` 接口可视为值与名称、类型和地址。  `IDebugReference2`，另一方面，可视为类型和地址。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)