---
title: "IDebugDefaultPort2 | Microsoft Docs"
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
  - "IDebugDefaultPort2"
helpviewer_keywords: 
  - "IDebugDefaultPort2 接口"
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口提供了几个用于访问端口的服务器和通知结构。  
  
## 语法  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## 实现者说明  
 Visual Studio 实现此接口表示访问的程序的调试端口。  自定义端口提供程序还可以实现此接口，则它处理远程调试。  
  
## 调用方的说明  
 对方法的参数。 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) 接口提供此接口。  调用 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 还可以获取此接口。  
  
## 方法按 Vtable 顺序  
 除了在 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)定义的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md)|从此端口获取端口通知接口。|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|具有接口承载此端口的服务器。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|确定此端口是否在本地计算机上运行。|  
  
## 备注  
 ，因为它不表示默认端口，名称 “`IDebugDefaultPort2`”是错误的名称的位。  它可称为 “IDebugPort3”。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)