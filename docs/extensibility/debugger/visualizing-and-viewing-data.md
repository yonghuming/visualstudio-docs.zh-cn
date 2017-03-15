---
title: "可视化和查看数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，查看数据"
  - "调试 [调试 SDK]，实现数据可视化"
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 可视化和查看数据
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

键入可视化工具和自定义浏览器当前数据使用快速是对开发人员的方法。  表达式计算器 \(EE\)可以支持第三方类型可视化工具以及提供自己的自定义浏览器。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 多少类型可视化工具和自定义浏览器与目标类型通过调用 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) 方法。  如果具有类型的可视化工具或提供至少自定义的浏览器， Visual Studio 会调用 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 方法检索这些可视化工具和浏览器列表 \(实际上， `CLSID`实现可视化工具和浏览器\) 的列表并将它们提供给用户。  
  
## 支持类型可视化工具  
 具有 EE 必须实现支持类型可视化工具的接口。  这些接口可以分解为两大类:列出该类型可视化工具以及访问属性的数据进行一些。  
  
### 列表类型可视化工具  
 EE 支持列表在其 `IDebugProperty3::GetCustomViewerCount` 和 `IDebugProperty3::GetCustomViewerList`的实现的类型可视化工具。  这些方法通过调用相应的方法 [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) 和 [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)。  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) 通过调用 [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)获取。  此方法要求 [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) 接口，从 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 接口来获得传递给 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。  `IEEVisualizerServiceProvider::CreateVisualizerService` 还需要传递给 `IDebugParsedExpression::EvaluateSync`的 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) 和 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 接口。  所需的最终接口创建 `IEEVisualizerService` 接口是 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 接口， EE 实现。  此接口允许更改对可视化的属性。  所有属性数据在 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 接口封装，由 EE 还实现。  
  
### 访问数据的属性  
 访问数据的属性通过 [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) 接口完成。  若要获取此接口， Visual Studio 缩放在属性获取对象的 [QueryInterface](/visual-cpp/atl/queryinterface)[IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) 接口 \(实现在同一对象实现 [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) 接口\) 然后调用 [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 方法获取 `IPropertyProxyEESide` 接口。  
  
 所有数据传递到和在 `IPropertyProxyEESide` 接口之外在 [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) 接口中封装。  此接口表示字节并由 Visual Studio et\-ee 实现。  当将更改时特性的数据， Visual Studio 创建包含新数据的一 `IEEDataStorage` 对象并调用与的 [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) 数据对象以获取，因此，传递给 [InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md) 更新属性的数据的新 `IEEDataStorage` 对象。  `IPropertyProxyEESide::CreateReplacementObject` 允许 EE 实例化实现接口 `IEEDataStorage` 自己的类。  
  
## 支持自定义浏览器  
 标志 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` 在 `dwAttrib` 设置 [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) 结构字段 \(返回调用 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)\) 指示对象具有自定义浏览器与它。  在此标志设置为时，使用 [QueryInterface](/visual-cpp/atl/queryinterface)， Visual Studio 从 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 接口的 [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) 接口。  
  
 如果用户选择自定义浏览器， Visual Studio 将实例化自定义浏览器使用 `IDebugProperty3::GetCustomViewerList` 方法提供的浏览器的 `CLSID` 。  Visual Studio 然后调用 [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) 显示值给用户。  
  
 通常， `IDebugCustomViewer::DisplayValue` 显示数据的只读视图。  若要允许对数据所做的更改， EE 必须实现支持有关属性对象的更改数据的自定义接口。  `IDebugCustomViewer::DisplayValue` 方法使用此自定义接口支持更改数据。  方法查找在 `pDebugProperty` 作为参数传递给方法的 `IDebugProperty2` 接口的自定义接口。  
  
## 支持类型可视化工具和自定义浏览器  
 EE 可以支持类型可视化工具和在 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) 和 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 方法的自定义浏览器。  首先， EE 将它提供给 [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) 方法返回的值自定义浏览器的数目。  接下来， EE 追加 `CLSID`自己的自定义浏览器保存到 [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) 方法返回的列表。  
  
## 请参阅  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)   
 [类型的可视化工具和自定义查看器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)