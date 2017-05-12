---
title: "IApplicationDebugger 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IApplicationDebugger 接口"
ms.assetid: 27f6f8f5-2bf3-49bc-8abb-dfca98935aba
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger 接口
调试器显示的主要接口。  除了从 `IUnknown` 继承的方法之外，`IApplicationDebugger` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IApplicationDebugger::QueryAlive](../../winscript/reference/iapplicationdebugger-queryalive.md)|指示调试器是否具有响应能力。|  
|[IApplicationDebugger::CreateInstanceAtDebugger](../../winscript/reference/iapplicationdebugger-createinstanceatdebugger.md)|允许对象的创建在调试器中由进程外到调试器的代码。|  
|[IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)|处理调试输出事件。|  
|[IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)|处理断点事件。|  
|[IApplicationDebugger::onClose](../../winscript/reference/iapplicationdebugger-onclose.md)|处理调试应用程序关闭事件。|  
|[IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)|处理自定义应用程序事件。|