---
title: "IDebugArrayObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject"
helpviewer_keywords: 
  - "IDebugArrayObject 方法"
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口表示一个数组对象。  
  
## 语法  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## 实施者注意事项  
 表达式计算器实现此接口来表示一个数组。  
  
## 调用方的说明  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 接口通过使用可以获得此接口 [QueryInterface](/visual-cpp/atl/queryinterface) 如果该对象表示一个数组。  
  
## Vtable 顺序中的方法  
 除了上方法 `IDebugObject` 接口，将以下方法实现上 `IDebugArrayObject` 接口。  
  
|方法|描述|  
|--------|--------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|获取数组中元素的计数。|  
|[GetElement](../Topic/IDebugArrayObject::GetElement.md)|获取数组的元素。|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|获取数组的所有元素。|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|获取数组的秩。|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|获取数组的维数。|  
  
## 备注  
 表达式计算器使用此接口来表示分析树中的数组。  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)