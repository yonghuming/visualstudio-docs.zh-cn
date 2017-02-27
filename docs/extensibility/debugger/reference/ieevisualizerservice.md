---
title: "IEEVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService"
helpviewer_keywords: 
  - "IEEVisualizerService 接口"
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IEEVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口实现提供功能的主要方法 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 和 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 接口。  
  
## 语法  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## 实施者注意事项  
 Visual Studio 实现此接口以允许的表达式计算器 \(EE\) 来支持类型的可视化工具。  
  
## 调用方的说明  
 EE 调用 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) 此接口作为其支持的一部分获取类型的可视化工具。  
  
## Vtable 顺序中的方法  
  
|方法|描述|  
|--------|--------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|检索有关哪些知道此服务的自定义查看器的数目。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|检索自定义查看器的列表。|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|返回一个代理对象的属性。|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|检索值字符串以显示指定的属性或字段的数目。|  
  
## 备注  
 IDE 将使用 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 接口，以确定是否有任何自定义查看器，或键入属性的可视化工具。 通过创建可视化工具服务 \(与 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\)，EE 可以提供与功能 `IDebugProperty3` 和 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) （支持查看和更改属性的值） 接口，从而支持类型的可视化工具。  
  
 如果 EE 具有自定义查看器本身实现，可以将附加 EE `CLSID`s 到返回的列表的末尾这些自定义查看器 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)。 这允许 EE 以支持其自己的自定义查看器以及类型的可视化工具。 请务必确保 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) 反映添加任何自定义查看器。  
  
 请参阅 [类型的可视化工具和自定义查看器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 可视化工具和查看器之间的差异的讨论。  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [类型的可视化工具和自定义查看器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)