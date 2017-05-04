---
title: "IMachineDebugManagerCookie 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerCookie 接口"
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie 接口
类似于 `IMachineDebugManager` 接口，`IMachineDebugManagerCookie` 接口支持调试cookie。  
  
 此接口\(与 `IDebugCookie` 接口。\)在脚本调试器允许脚本进程中运行，而无需调试器记录这些脚本。  
  
 脚本调试器调用进程中的 `IDebugCookie::SetDebugCookie` 方法调试管理器\(PDM\)。  然后，PDM与所有请求添加一起发送此cookie使用 `IMachineDebugManagerCookie` 接口的方法，或移除脚本应用程序能够与设备调试管理器\(MDM\)，。  MDM然后通知更改的每个调试器，但具有该cookie的脚本。  
  
 除了从 `IUnknown` 继承的方法之外，`IMachineDebugManagerCookie` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|添加一个应用程序向运行的应用程序列表中。|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|返回当前的枚举数列表运行应用程序。|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|从运行的应用程序中移除应用程序列表中。|  
  
## 请参阅  
 [IMachineDebugManager 接口](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie 接口](../../winscript/reference/idebugcookie-interface.md)