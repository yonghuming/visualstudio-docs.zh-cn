---
title: "IEEDataStorage | Microsoft Docs"
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
  - "IEEDataStorage"
helpviewer_keywords: 
  - "IEEDataStorage 接口"
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEDataStorage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示字节。  
  
## 语法  
  
```  
IEEDataStorage : IUnknown  
```  
  
## 实现者说明  
 表达式计算器 \(EE\)实现此接口表示字节 \(用于按类型可视化工具。 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 接口检索和更改数据\)。  EE 通常实现此接口支持外部类型可视化工具。  
  
## 调用方的说明  
 在 `IPropertyProxyEESide` 接口的方法都返回此接口。  调用 [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 获取 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 接口。  调用 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) 接口。  
  
## 方法按 Vtable 顺序  
 `IEEDataStorage` 接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetData](../Topic/IEEDataStorage::GetData.md)|检索数据字节的指定数目到提供的缓冲区。|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|检索数据的字节数。可用。|  
  
## 备注  
 此接口由与特定对象容纳的访问数据的类型可视化工具使用。  该数据将字节，使类型可视化工具操纵在任何方式需要显示给用户。  
  
 ，如果需要，自定义浏览器也可以使用此接口，虽然常见，自定义浏览器将使用自定义接口、 [GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md) 或 [GetStringChars](../Topic/IDebugProperty3::GetStringChars.md) \(对于字符串面向数据\)。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [类型的可视化工具和自定义查看器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)