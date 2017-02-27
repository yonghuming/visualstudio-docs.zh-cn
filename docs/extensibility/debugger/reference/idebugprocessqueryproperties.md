---
title: "IDebugProcessQueryProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessQueryProperties"
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口是 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 实现的扩展接口。  它允许有关调试的实现获取处理器环境。  
  
## 语法  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## 实现者说明  
 实现有关调试的执行环境的此接口获取处理器。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugProcessQueryProperties`方法。  
  
|方法|说明|  
|--------|--------|  
|[QueryProperty](../Topic/IDebugProcessQueryProperties::QueryProperty.md)|属性值的查询。|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|属性值的查询。|  
  
## 备注  
 此接口只需实现。  
  
## 要求  
 标题:Portpriv.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)