---
title: "IDebugCoreServer2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2"
helpviewer_keywords: 
  - "IDebugCoreServer2 接口"
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口用于表示和从一台服务器的信息在网络上的计算机。  
  
## 语法  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## 实现者说明  
 Visual Studio 实现此接口表示该服务器。  Visual Studio 每个实例创建此接口的实例。  
  
## 调用方的说明  
 自定义端口提供程序接收调用此接口来 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)。  
  
 调试引擎可以通过返回 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)的调用间接获取此接口添加到 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) \(， `IDebugCoreServer2`从派生的接口\)。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugCoreServer2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)|获取计算机的名称和属性。|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|获取计算机的名称。|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|获取计算机上存在的端口提供程序。|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|获取计算机上已存在的端口。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|创建任何端口的枚举数计算机上。|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|创建任何端口提供程序的枚举数计算机上。|  
|[GetMachineUtilities\_V7](../Topic/IDebugCoreServer2::GetMachineUtilities_V7.md)|获取设备的设备实用工具。|  
  
## 备注  
 Visual Studio 还用于此接口浏览进程运行在网络上的计算机。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)