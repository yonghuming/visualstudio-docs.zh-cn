---
title: "IDebugSessionProviderEx 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugSessionProviderEx 接口
主界面由调试器IDE提供使宿主和语言启动调试。  生成它正在运行的应用程序的调试会话。  此接口由设备调试管理器。  
  
 除了从 `IUnknown` 继承的方法之外，`IDebugSessionProviderEx` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|确定实时\(jit\)调试是否为指定的应用程序是可能的。|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|启动与指定的应用程序的调试会话。|