---
title: "IDebugDynamicFieldCOMPlus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDynamicFieldCOMPlus 接口"
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugDynamicFieldCOMPlus
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 对象的动态字段。  
  
## 语法  
  
```  
IDebugDynamicFieldCOMPlus : IDebugDynamicField  
```  
  
## 方法  
 除了在 [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) 接口的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|检索给定的类型其原始类型。|  
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|检索给定的类型其标记。|  
  
## 要求  
 标题:Sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll