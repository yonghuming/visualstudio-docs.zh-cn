---
title: "IDebugPortRequest2 | Microsoft Docs"
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
  - "IDebugPortRequest2"
helpviewer_keywords: 
  - "IDebugPortRequest2 接口"
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口描述一个端口。  此声明用于将端口添加到端口提供程序。  
  
## 语法  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## 实现者说明  
 Visual Studio 在获取调试端口过程中通常实现此接口从端口提供程序。  
  
## 调用方的说明  
 此接口传递给 [添加端口](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 创建调试端口。  为 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) 的调用返回此接口，表示用于的请求首先创建端口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugPortRequest2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|获取端口的名称创建。|  
  
## 备注  
 调试引擎与端口提供程序通常不进行交互，并不需要此接口。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [添加端口](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)