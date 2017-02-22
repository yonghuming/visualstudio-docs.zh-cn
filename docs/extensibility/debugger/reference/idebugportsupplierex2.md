---
title: "IDebugPortSupplierEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierEx2 接口"
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplierEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

提供支持将端口提供程序可以与内核服务器选择并与之交互。  
  
## 语法  
  
```  
IDebugPortSupplierEx2 : IUnknown  
```  
  
## 实现者说明  
 自定义端口提供程序实现此接口，以便可以选择核心服务器使用。  
  
## 方法  
 下表显示 **IDebugPortSupplierEx2**方法。  
  
|方法|说明|  
|--------|--------|  
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|将端口提供程序的核心服务器。|  
  
## 要求  
 标题:Portpriv.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)