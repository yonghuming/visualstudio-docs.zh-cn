---
title: "IDebugObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject"
helpviewer_keywords: 
  - "IDebugObject 接口"
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口表示联编程序创建用于封装符号和表达式的值的对象。  
  
## 语法  
  
```  
IDebugObject : IUnknown  
```  
  
## 实施者注意事项  
 表达式计算器实现此接口，以表示的对象。  
  
## 调用方的说明  
 此接口是表达式计算器分析表达式中使用的所有对象的基类。 返回通过调用 [将绑定](../../../extensibility/debugger/reference/idebugbinder-bind.md) 方法。[QueryInterface](/visual-cpp/atl/queryinterface) 此接口中获取更多专用的接口。  
  
## Vtable 顺序中的方法  
 下表显示的方法 `IDebugObject`。  
  
|方法|描述|  
|--------|--------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|获取该对象的大小。|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|获取对象的值作为一系列连续的字节。|  
|[SetValue](../Topic/IDebugObject::SetValue.md)|从一系列连续的字节设置的对象的值。|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|设置此对象的引用值。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|获取表示对象的值的地址的内存上下文。|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|调试引擎的地址空间中创建托管对象的副本。|  
|[IsNullReference](../Topic/IDebugObject::IsNullReference.md)|测试此对象是否为空引用。|  
|[IsEqual](../Topic/IDebugObject::IsEqual.md)|将与此对象进行比较。|  
|[为只读](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|确定此对象是否为只读的。|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|确定该对象是透明的代理。|  
  
## 备注  
 表达式计算器使用该接口作为基类，用于表示分析树中的对象。  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../Topic/IDebugArrayObject::GetElement.md)   
 [将绑定](../../../extensibility/debugger/reference/idebugbinder-bind.md)