---
title: "IDebugProgramNode2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2"
helpviewer_keywords: 
  - "IDebugProgramNode2 接口"
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示可调试的程序。  
  
## 语法  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)或自定义端口提供程序实现此接口可表示正在调试的程序。  此接口在同一对象通常是实现 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口。  此接口通过调用 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)注册 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 。  
  
## 调用方的说明  
 调用 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) 返回此接口。  自定义端口提供程序通过调用接收此接口来 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。  DE 通过调用接收此接口来 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugProgramNode2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|获取程序的名称。|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|获取承载程序的进程的名称。|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|获取系统处理承载程序的进程的标识符。|  
|[GetHostMachineName\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|已弃用。  不要使用。|  
|[Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|已弃用。  不要使用。  为一种替代方法参见 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 接口。|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|获取运行此程序的 DE 的名称和标识符。|  
|[DetachDebugger\_V7](../Topic/IDebugProgramNode2::DetachDebugger_V7.md)|已弃用。  不要使用。|  
  
## 备注  
 会议调试管理器 \(SDM\)通常会调用 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) 获取此接口。  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)