---
title: "IDebugPort2 | Microsoft Docs"
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
  - "IDebugPort2"
helpviewer_keywords: 
  - "IDebugPort2 接口"
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示设备的调试端口。  
  
## 语法  
  
```  
IDebugPort2 : IUnknown  
```  
  
## 实现者说明  
 自定义端口提供程序实现此接口表示设备的调试端口。  
  
 如果端口支持发送端口操作，则还必须实现 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 接口支持又提供 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) 接口的 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 接口。  
  
## 调用方的说明  
 调用 [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) 或 [添加端口](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 返回此接口，则表示请求的端口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugPort2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|返回端口的名称。|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|返回端口标识符。|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|返回用于的请求创建端口 \(如果有\)。|  
|[GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)|返回此的端口提供程序。|  
|[GetProcess](../Topic/IDebugPort2::GetProcess.md)|返回接口为给定进程进程的标识符。|  
|[EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)|枚举上运行的所有进程端口。|  
  
## 备注  
 本地端口提供对所有进程并运行在本地计算机上的程序。  其他端口可能表示与基于 windows CE 的计算机的串行电缆连接或与非 DCOM 计算机的网络连接。  `IDebugPort2` 接口用于查找端口的名称和标识符，枚举上运行的所有进程端口，并为生成提供功能，并且终止在端口处理。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)