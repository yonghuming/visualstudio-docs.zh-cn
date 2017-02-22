---
title: "IDebugPortNotify2 | Microsoft Docs"
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
  - "IDebugPortNotify2"
helpviewer_keywords: 
  - "IDebugPortNotify2 接口"
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

程序可以使用调试端口运行它的此接口注册或注销。  
  
## 语法  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## 实现者说明  
 自定义端口提供程序实现此接口支持添加和移除程序从端口。  在同一对象通常是实现 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 接口。  
  
## 调用方的说明  
 为 [QueryInterface](/visual-cpp/atl/queryinterface) 的调用在 `IDebugPort2` 接口返回此接口。  此外，对于 [GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md) 的调用返回此接口。  调试引擎可以看到此接口作为参数传递给 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugPortNotify2`方法。  
  
|方法|说明|  
|--------|--------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|程序可以使用调试端口运行它的注册。|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|程序可以从该端口在调试运行它的注销。|  
  
## 备注  
 除非调试端口使用一种知道程序何时加载或卸载，自定义端口提供程序必须实现此接口。  为调试加载通过特定端口使用此接口，的所有过程中进行跟踪。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)