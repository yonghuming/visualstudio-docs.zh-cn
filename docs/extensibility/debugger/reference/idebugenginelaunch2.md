---
title: "IDebugEngineLaunch2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineLaunch2
helpviewer_keywords: IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 989bea1fc3398be376c7c2d5c41ce390e59c228f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
由调试引擎 (DE) 用于启动和终止程序。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 如果它具有用于启动的进程，不能完全由自定义端口处理的特殊要求，将通过自定义 DE 实现此接口。 这通常是这种情况，当 DE 是解释器的一部分，正在调试的进程是一个脚本： 解释器应具有可首先，启动，然后加载和启动脚本。 端口可以启动解释器，但该脚本可能需要特殊处理 （这是其中 DE 具有的角色）。 仅在没有启动自定义端口不能处理程序的唯一要求被实现此接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 此接口由会话调试管理器 (SDM) 如果 SDM 可以获得此接口从[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)接口 （使用 QueryInterface）。 如果可以获得此接口，SDM 知道 DE 具有特殊要求，并且调用此接口来启动程序而不是让启动它的端口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugEngineLaunch2`。  
  
|方法|描述|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|通过 DE 启动进程。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|继续处理执行。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|确定是否可以终止进程。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|终止进程。|  
  
## <a name="requirements"></a>要求  
 标头： Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)