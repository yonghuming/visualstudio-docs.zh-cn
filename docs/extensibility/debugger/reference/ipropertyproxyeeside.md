---
title: "IPropertyProxyEESide | Microsoft Docs"
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
  - "IPropertyProxyEESide"
helpviewer_keywords: 
  - "IPropertyProxyEESide 接口"
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口提供了视图数据在关联的对象。  此接口是支持的一部分类型的可视化工具。  
  
## 语法  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## 实现者说明  
 表达式计算器实现此接口支持类型可视化工具。  
  
## 调用方的说明  
 调用 [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 获取此接口。  调用 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) 接口。  
  
## 方法按 Vtable 顺序  
 以下方法由此接口实现:  
  
|方法|说明|  
|--------|--------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|初始化数据源提供程序，以便对象的数据进行访问。|  
|[GetManagedViewerCreationData](../Topic/IPropertyProxyEESide::GetManagedViewerCreationData.md)|检索有关对象的程序集的信息。|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|获取初始数据。对象。|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|创建现有数据存储的副本。|  
|[InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md)|创建对现有数据存储。|  
|[ResolveAssemblyRef](../Topic/IPropertyProxyEESide::ResolveAssemblyRef.md)|在包含此对象的程序集上下文检索有关特定程序集的信息。|  
  
## 备注  
 类型可视化工具使用此接口来与对象关联的值的访问此接口是的一部分。  数据会通过 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 接口时，提供数据的只读视图。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [类型的可视化工具和自定义查看器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)