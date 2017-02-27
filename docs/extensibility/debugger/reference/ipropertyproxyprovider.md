---
title: "IPropertyProxyProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyProvider"
helpviewer_keywords: 
  - "IPropertyProxyProvider 接口"
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口提供一个代理界面查看并更改对象的数据。  
  
## 语法  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## 实现者说明  
 表达式计算器 \(EE\)实现在同一对象的此接口作为 EE'S 的一部分 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 接口支持类型可视化工具的实现。  
  
## 调用方的说明  
 调用 `IDebugProperty3` 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取此接口。  
  
## 方法按 Vtable 顺序  
 `IPropertyProxyProvider` 接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|检索属性代理界面查看有关对象的数据。|  
  
## 备注  
 虽然 EE 实现此接口， [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 的实现。 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)通常处理。  请参见 [可视化和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md) 有关获取 IEEVisualizerService 接口的详细信息。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [类型的可视化工具和自定义查看器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [可视化和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md)