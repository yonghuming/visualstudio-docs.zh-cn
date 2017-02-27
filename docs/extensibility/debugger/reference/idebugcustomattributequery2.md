---
title: "IDebugCustomAttributeQuery2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttributeQuery2"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery 接口"
  - "IDebugCustomAttributeQuery2 接口"
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugCustomAttributeQuery2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

确定自定义特性的存在此字段的，则为; 如果存在，则返回属性信息。  
  
## 语法  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## 实现者说明  
 符号提供程序实现在同一对象的此接口实现 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 为了支持自定义特性。  
  
## 调用方的说明  
 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 从 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 接口的此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 **IDebugCustomAttributeQuery** 接口的方法。  
  
|方法|说明|  
|--------|--------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|确定自定义特性名称是否存在。|  
|[GetCustomAttributeByName](../Topic/IDebugCustomAttributeQuery2::GetCustomAttributeByName.md)|获取给定自定义的属性信息。|  
  
 除了 **IDebugCustomAttributeQuery** 方法之外， `IDebugCustomAttributeQuery2` 执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|获取所有自定义特性的枚举器附加到此字段。|  
  
## 备注  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) 方法可能会返回了该字段定义的任何自定义属性的枚举数。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)