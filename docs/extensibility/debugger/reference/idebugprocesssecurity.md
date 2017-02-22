---
title: "IDebugProcessSecurity | Microsoft Docs"
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
  - "IDebugProcessSecurity 接口"
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`IDebugProcessSecurity` 由端口提供程序实现警告用户附加到进程是不安全的。  
  
## 语法  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugProcessSecurity`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|从端口提供程序获取用户名。|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|警告附加到调试进程是不安全的用户。|  
  
## 备注  
 实现此接口公开警告并允许用户取消，如果附加的进程可被视为不安全。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [端口](../../../extensibility/debugger/ports.md)   
 [端口供应商](../../../extensibility/debugger/port-suppliers.md)   
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)