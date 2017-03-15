---
title: "IDebugFunctionObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject"
helpviewer_keywords: 
  - "IDebugFunctionObject 接口"
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugFunctionObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口表示一个函数。  
  
## 语法  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## 实施者注意事项  
 表达式计算器实现此接口来表示一个函数。  
  
## 调用方的说明  
 此接口是专用化 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 接口，并使用获取 [QueryInterface](/visual-cpp/atl/queryinterface) 上 `IDebugObject` 接口。  
  
## Vtable 顺序中的方法  
 除了从继承的方法 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), 、 `IDebugFunctionObject` 接口公开下列方法。  
  
|方法|描述|  
|--------|--------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|创建一个基元数据对象。|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|创建使用构造函数的对象。|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|使用没有构造函数创建的对象。|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|创建一个数组对象。|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|创建一个字符串对象。|  
|[评估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|调用该函数并返回作为对象生成的值。|  
  
## 备注  
 此接口使表达式计算器来表示在分析树中的函数。`Create` 使用此接口中的方法来构造对象表示对方法的输入的参数。 然后可以通过调用执行函数 [评估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 方法，它返回一个表示该函数的返回值的对象。  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)