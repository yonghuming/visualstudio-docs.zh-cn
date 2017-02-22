---
title: "IDebugBinder3 | Microsoft Docs"
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
  - "IDebugBinder3"
helpviewer_keywords: 
  - "IDebugBinder3 接口"
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口提供对类型、 别名和自定义可视化工具服务的访问。  
  
## 语法  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## 实施者注意事项  
 调试引擎可以实现此接口以支持别名、 自定义可视化工具服务和访问的对象类型信息。  
  
## 调用方的说明  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 接口获得此接口通过使用 [QueryInterface](/visual-cpp/atl/queryinterface)。  
  
## Vtable 顺序中的方法  
 除了提供的方法 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 接口，此接口实现了下列︰  
  
|方法|描述|  
|--------|--------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|检索表示此对象绑定到的内存的内存对象。|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|检索此对象 （如果有），与关联的异常|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|检索在给定其名称的别名|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|检索此对象的所有别名的数组|  
|[GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md)|获取与此对象关联的参数类型的数目|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|检索与此对象关联的参数类型的列表|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|获取到可视化工具服务时接口|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|将对象位置或 64 位内存地址转换为内存上下文中。|  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)