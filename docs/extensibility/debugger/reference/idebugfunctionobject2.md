---
title: "IDebugFunctionObject2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2 接口"
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表示一个函数，并增强 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 接口。  
  
## 语法  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## 实施者注意事项  
 表达式计算器 \(EE\) 实现此接口来表示一个函数。  
  
## 调用方的说明  
 此接口的方法将推迟的 **IDebugFunctionObject** 通过以下方式︰  
  
-   **IDebugEvaluate** 方法采用标志。  
  
-   **CreateObject** 方法采用标志和超时。  
  
-   **CreateStringObjectWithLength** 方法采用一个长度。  
  
## 方法  
 此接口实现的以下方法︰  
  
|方法|描述|  
|--------|--------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|创建使用给定评估标志设置和超时值的构造函数的对象。|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|创建一个具有指定的长度的字符串对象。|  
|[评估](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|调用该函数并返回作为对象生成的值。|  
  
## 要求  
 标头︰ Ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll