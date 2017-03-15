---
title: "IDebugPortSupplierLocale2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierLocale2 接口"
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugPortSupplierLocale2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

提供区域设置将用于端口提供支持。  
  
## 语法  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## 实现者说明  
 自定义端口提供程序实现此接口设置区域设置。  
  
## 方法  
 下表显示 **IDebugPortSupplierLocale2**方法。  
  
|方法|说明|  
|--------|--------|  
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|将端口提供程序的区域设置。|  
  
## 要求  
 标题:Portpriv.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)