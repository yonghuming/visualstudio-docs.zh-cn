---
title: "IDebugAlias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias"
helpviewer_keywords: 
  - "IDebugAlias 接口"
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表示一个变量的数值别名。 别名是只是一个变量的其他名称。  
  
## 语法  
  
```  
IDebugAlias : IUnknown  
```  
  
## 实施者注意事项  
 表达式计算器 \(EE\) 实现此接口以支持变量数字别名。  
  
## 调用方的说明  
 [CreateAlias](../Topic/IDebugObject2::CreateAlias.md) 创建特定对象的别名。 若要搜索的别名，请使用 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) 或 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)。  
  
## Vtable 顺序中的方法  
 在中定义以下方法 `IDebugAlias` 接口。  
  
|方法|描述|  
|--------|--------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|获取此别名所引用的对象。|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|获取别名名称。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|检索 `ICorDebugValue` 接口提供对访问托管代码对此对象 \(仅适用于托管代码\) 的信息。|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|将其标记别名为不再使用。|  
  
## 备注  
 别名是以字符串形式的 \# 字符，例如，1001 \# 后跟十进制数。  
  
## 要求  
 标头: ee.h  
  
 命名空间: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../Topic/IDebugObject2::CreateAlias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)