---
title: "IRemoteDebugApplicationEx 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx 接口"
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx 接口
表示正在运行的应用程序。  它不必对应于操作系统进程。  通常，调试器以进行调试。  进程内调试管理器通常实现应用程序对象。  
  
 除了从 `IUnknown` 继承的方法之外，`IRemoteDebugApplicationEx` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|返回宿主应用程序的进程ID。|  
|GetHostMachineName|返回上宿主应用程序运行在计算机的名称。|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|设置调试器本地化的语言。|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|强制调试器附加到的单步模式。|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|取消中断命令。|  
|SetProxyBlanketAndAddRef|更新COM有关一个代理的安全信息调试器对象的可以确保与远程调试的兼容性从基于Windows 95操作系统。|  
|ReleaseFromSetProxyBlanket|从SetProxyBlanketAndAddRef的版本AddRef。|