---
title: "IEEVisualizerDataProvider | Microsoft Docs"
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
  - "IEEVisualizerDataProvider"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider 接口"
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口提供能够更改通过类型可视化工具的对象的值。  
  
## 语法  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## 实施者注意事项  
 表达式计算器实现此接口以支持在类型可视化工具通过属性对象上修改数据。  
  
## 调用方的说明  
 此接口可用于创建 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 对象，通过调用 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)。 有关详细信息，请参见 [可视化和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md)。  
  
## Vtable 顺序中的方法  
  
|方法|描述|  
|--------|--------|  
|[CanSetObjectForVisualizer](../Topic/IEEVisualizerDataProvider::CanSetObjectForVisualizer.md)|确定是否可以更新此对象 （或以后，它的值），表示此可视化工具。|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|为此可视化工具将强制重新评估的对象。|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|获取此可视化工具 （完成的不是计算） 的现有对象。|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|为此可视化工具，从而更改该可视化工具显示的值更新对象。|  
  
## 备注  
 可视化工具服务 \(由表示 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 接口，并返回 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\) 保留对对象实现引用 `IEEVisualizerDataProvider` 接口。 因此， `IEEVisualizerDataProvider` 不应实现的相同对象上实现接口 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 如果该对象维护的引用 `IEEVisualizerService` 对象︰ 发生循环引用，并在对象被销毁时，会发生死锁。 建议的方法是实现 `IEEVisualizerDataProvider` 到一个单独的对象上 `IDebugProperty2` 对象而不调用的委托 `IUnknown::AddRef` 在其上。  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [可视化和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md)