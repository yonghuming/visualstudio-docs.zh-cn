---
title: "IDebugCustomAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute"
helpviewer_keywords: 
  - "IDebugCustomAttribute 接口"
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示自定义特性，因此，它可以提供属性的名称、父节点和类类型。  
  
## 语法  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## 实现者说明  
 符号提供程序实现此接口以便支持自定义特性与符号。  它是您通常实现的对象。  
  
## 调用方的说明  
 为 [下一步](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) 的调用返回此接口。  为 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) 方法的调用返回 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) 接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugCustomAttribute`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetParentField](../Topic/IDebugCustomAttribute::GetParentField.md)|获取当前属性附加字段。|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|获取自定义特性类类型。|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|获取自定义属性的名称。|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|获取属性信息作为字节 blob。|  
  
## 备注  
 自定义特性是提供自定义元数据与特定的类或方法 C\# 的结构。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)