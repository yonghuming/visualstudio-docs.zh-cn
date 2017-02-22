---
title: "IDebugFirewallConfigurationCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFirewallConfigurationCallback2 接口"
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

允许使用 DCOM 请求 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 确保的调试引擎，防火墙不会阻止远程调试。  
  
## 语法  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## 实现者说明  
 实现由该会话的端口对象调试管理器。  
  
## 方法  
 下表显示 `IDebugFirewallConfigurationCallback2`方法。  
  
|方法|说明|  
|--------|--------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|请求防火墙未阻止远程调试。|  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll