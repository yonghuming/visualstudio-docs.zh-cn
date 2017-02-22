---
title: "IEEVisualizerServiceProvider | Microsoft Docs"
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
  - "IEEVisualizerServiceProvider"
helpviewer_keywords: 
  - "IEEVisualizerServiceProvider 接口"
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerServiceProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口，可以创建一个可视化工具服务，它用于处理 IDE 类型可视化工具任务的方法访问。  
  
## 语法  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## 实施者注意事项  
 Visual Studio 实现此接口可创建一个可视化工具服务对象，又用于提供类 Id \(`CLSID`s\) 的类型为 Visual Studio IDE 的可视化工具。  
  
## 调用方的说明  
 表达式计算器 \(EE\) 调用 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) 以获取此接口。  
  
## Vtable 顺序中的方法  
  
|方法|描述|  
|--------|--------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|创建可视化工具服务|  
  
## 备注  
 `IEEVisualizerServiceProvider` 在实现过程中获取接口 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。 此接口创建的可视化工具服务用于提供与功能 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 接口，EE 负责实现。 EE 组件还负责实现 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 界面，使类型的可视化工具查看和修改属性的值。  
  
 请参阅 [可视化和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md) 有关这些接口的交互方式的详细信息。  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [可视化和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md)