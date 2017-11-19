---
title: "IRemoteDebugApplicationEx 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3360cea0d1649348a795356ad827b32b6f8ebc19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx 接口
表示正在运行的应用程序。 它不需要以与操作系统进程相对应。 通常情况下，调试器以目标用于调试的应用程序。 过程调试管理器通常实现应用程序对象。  
  
 除了从继承的方法`IUnknown`、`IRemoteDebugApplicationEx`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|返回主机应用程序的进程 ID。|  
|GetHostMachineName|返回运行主机应用程序的计算机的名称。|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|设置调试器本地化的语言。|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|强制为单步模式调试器。|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|撤消中断命令。|  
|SetProxyBlanketAndAddRef|更新上的调试器对象的代理，以确保与从基于 Windows 95 的操作系统进行远程调试的兼容性的 COM 安全信息。|  
|ReleaseFromSetProxyBlanket|从 SetProxyBlanketAndAddRef 版本 AddRef。|