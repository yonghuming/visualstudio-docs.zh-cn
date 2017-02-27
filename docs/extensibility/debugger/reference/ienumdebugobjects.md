---
title: "IEnumDebugObjects | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects"
helpviewer_keywords: 
  - "IEnumDebugObjects 接口"
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugObjects
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口表示实现的对象的集合 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 接口。  
  
## 语法  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## 实施者注意事项  
 表达式计算器实现此接口以提供多组实现的对象的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 接口。 请注意，这不是由于存在一个标准 COM 枚举 [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) 方法。  
  
## 调用方的说明  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) 返回此接口。  
  
## Vtable 顺序中的方法  
 此接口实现以下方法。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|检索下一套 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 枚举中的对象。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|跳过指定的数目的条目。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|将枚举重置为第一个条目。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|检索当前枚举的副本。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|检索在枚举中的条目数。|  
  
## 备注  
 此接口允许对一组的数组中的对象进行枚举的调试引擎。  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)