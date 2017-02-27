---
title: "IDebugPrimitiveTypeField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPrimitiveTypeField 接口"
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugPrimitiveTypeField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示基元类型从 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 接口的枚举值。  
  
## 语法  
  
```  
IDebugPrimitiveTypeField : IDebugField  
```  
  
## 方法  
 除了在 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 接口的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|检索原始类型与此字段。|  
  
## 要求  
 标题:Sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll