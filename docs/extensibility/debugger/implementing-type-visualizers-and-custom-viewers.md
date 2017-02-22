---
title: "实现自定义查看器以及类型的可视化工具 | Microsoft Docs"
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
  - "调试 [调试 SDK]，自定义查看器"
  - "调试 [调试 SDK]，类型的可视化工具"
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 实现自定义查看器以及类型的可视化工具
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 类型的可视化工具和自定义查看器允许用户查看特定类型的数据是数字的简单十六进制转储比更有意义的方式。 表达式计算器 \(EE\) 可以将自定义查看器与特定类型的数据或变量相关联。 由 EE 实现这些自定义查看器。 EE 还可以支持外部类型的可视化工具，可能来自另一个第三方供应商或甚至最终用户。  
  
## 讨论  
  
### 类型的可视化工具  
 Visual Studio 会要求类型的可视化工具和自定义查看器为每个对象将在监视窗口中显示的列表。 表达式计算器 \(EE\) 提供了这种类型的列表中每个它想要支持类型的可视化工具和自定义查看器。 调用 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) 和 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 启动整个进程的访问类型的可视化工具和自定义查看器 \(请参阅 [可视化和查看数据](../../extensibility/debugger/visualizing-and-viewing-data.md) 有关调用序列的详细信息\)。  
  
### 自定义查看器  
 自定义查看器在特定的数据类型为 EE 中实现，由表示 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 接口。 自定义查看器并不灵活类型可视化工具，因为只有当执行 EE 实现该特定的自定义查看器，它才可用。 实现自定义查看器是实现对类型的可视化工具的支持比简单得多。 但是，支持类型的可视化工具可以提供最大的灵活性向最终用户用于使他或她的数据可视化。 本次讨论中的其余部分涉及仅类型可视化工具。  
  
## 接口  
 EE 实现以下接口才能支持类型的可视化工具，可供 Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 EE 使用了以下接口来支持类型的可视化工具︰  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## 请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [可视化和查看数据](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)