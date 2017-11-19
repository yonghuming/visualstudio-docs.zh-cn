---
title: "通知端口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91bedf387fe86c2bf2fefb34e643e581a37c15bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="notifying-the-port"></a>通知端口
启动程序之后, 该端口必须要得到通知，，如下所示：  
  
1.  当一个端口收到新的程序节点时，它将程序创建事件发送回调试会话。 事件都带有一个表示该程序的接口。  
  
2.  调试会话查询可以将附加到调试引擎 (DE) 的标识符的程序。  
  
3.  调试会话检查 DE 为该程序允许 DEs 列表上。 调试会话获取此列表，从解决方案的活动程序设置，最初传递给它的调试包。  
  
     DE 必须是在允许列表中，否则 DE 将不会附加到程序。  
  
 以编程方式，当一个端口首次接收新的程序节点，它创建[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)接口来表示该程序。  
  
> [!NOTE]
>  不应与混淆这`IDebugProgram2`更高版本创建的调试引擎 (DE) 的接口。  
  
 端口发送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)回会话调试管理器 (SDM) 通过 COM 的程序创建事件`IConnectionPoint`接口。  
  
> [!NOTE]
>  不应与混淆这`IDebugProgramCreateEvent2`接口，由 DE 发出的更高版本。  
  
 端口事件接口本身，以及发送[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)， [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)，和[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)接口，表示端口，处理，并编程，分别。 SDM 调用[IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)若要获取可以调试程序，DE 的 GUID。 最初通过 GUID [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)接口。  
  
 SDM 检查 DE 允许 DEs 列表上。 SDM 从解决方案的活动程序设置，最初传递给它的调试包获取此列表。 DE 必须是在允许列表中，否则将不会附加到程序。  
  
 了解 DE 的标识后, SDM 已准备好将其附加到该程序。  
  
## <a name="see-also"></a>另请参阅  
 [启动程序](../../extensibility/debugger/launching-a-program.md)   
 [在启动后附加](../../extensibility/debugger/attaching-after-a-launch.md)   
 [调试任务](../../extensibility/debugger/debugging-tasks.md)