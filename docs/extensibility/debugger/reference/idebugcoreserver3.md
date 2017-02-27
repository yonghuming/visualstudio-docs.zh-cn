---
title: "IDebugCoreServer3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3"
helpviewer_keywords: 
  - "IDebugCoreServer3 接口"
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口允许对这些信息的访问有关进程运行的服务器。  
  
## 语法  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## 实现者说明  
 Visual Studio 实现此接口。  
  
## 调用方的说明  
 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 从 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 接口的此接口。  为 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) 的调用也能返回此接口。  自定义端口提供程序通常用于此接口启动服务器上的程序 \(本地或远程\)。  
  
## 方法按 Vtable 顺序  
 除了在 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 接口的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|检索服务器的名称。|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|检索服务器名称的一个友好版本|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|调用特定调试引擎会自动附加处理一些在进程启动。|  
|[DiagnoseWebDebuggingError](../Topic/IDebugCoreServer3::DiagnoseWebDebuggingError.md)|检索特定错误代码，以便自动附加失败。|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|创建一个调试引擎的实例上的。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|检索指示服务器是否的标志在计算机和调用方相同。|  
|[GetConnectionProtocol](../Topic/IDebugCoreServer3::GetConnectionProtocol.md)|检索指示协议的值使用与服务器通信。|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|禁用所有自动附加的所有设置调试此服务器了解的引擎。|  
  
## 备注  
 自定义端口提供程序接收调用 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 接口访问 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)。  `IDebugCoreServer3` 接口可从该接口来获得。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)