---
title: "类型的可视化工具和自定义查看器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，自定义查看器"
  - "调试 [调试 SDK]，类型的可视化工具"
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 类型的可视化工具和自定义查看器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

类型可视化工具是显示数据部分是一项非常具体的格式的元素。  此格式完全由可视化工具的实现，假如是最终用户或可视化工具的第三方供应商。  
  
 自定义浏览器是显示数据部分是一项非常具体的格式自定义表达式计算器的一部分。  此格式完全由该自定义浏览器的实现，这样，这意味着格式由表达式计算器的实现 \(EE\)。  
  
## 为表达式计算器的类型可视化工具支持  
 EE 可以通过支持支持类型可视化工具组接口可访问的可视化工具:接口例如 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) 和 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)。  然而，请注意， EE 不负责实现该类型可视化工具:EE 仅允许访问其类型信息的外部可视化工具访问。  这种可视化工具可能与 EE 一起被传送和在 Visual Studio 中的适当位置安装，提供另一个第三方供应商甚至由最终用户。  
  
## 为表达式计算器的自定义浏览器支持  
 EE 控件还支持 EE 提供查看的数据类型代码的自定义浏览器。  自定义浏览器 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 实现接口，处理数据显示所有负责任何格式希望;该浏览器对该显示的完全控制，并且甚至可能允许修改数据。  ，随着产品交付时， EE 提供的任何自定义浏览器附带了 EE。  
  
## 请参阅  
 [调试程序组件](../../extensibility/debugger/debugger-components.md)   
 [表达式计算器](../../extensibility/debugger/expression-evaluator.md)   
 [调试引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)