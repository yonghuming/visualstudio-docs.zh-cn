---
title: "IDebugPropertyField | Microsoft Docs"
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
  - "IDebugPropertyField"
helpviewer_keywords: 
  - "IDebugPropertyField 接口"
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPropertyField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口提供允许获取和设置属性的功能。  
  
## 语法  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## 实现者说明  
 符号提供程序实现在同一对象的此接口实现 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)。  此接口是支持属性的概念以及型类的专用化。  
  
## 调用方的说明  
 ，如果 [GetKind](../Topic/IDebugField::GetKind.md) 方法返回 `FIELD_KIND_PROP`，请使用 [QueryInterface](/visual-cpp/atl/queryinterface) 从 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 接口的此接口。  
  
## 方法按 Vtable 顺序  
 除了在 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 和 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 接口的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|获取获取属性的方法。|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|获取设置属性的方法。|  
  
## 备注  
 属性是托管代码概念并表示将变量的方法。  属性不存在于非托管 C\+\+。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)