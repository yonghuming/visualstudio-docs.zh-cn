---
title: "IDebugApplication110 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110 接口"
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110 接口
`IDebugApplication110` 接口扩展 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)的功能。  通过调用 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)的实现的QI可以获取此接口的实例。  
  
> [!IMPORTANT]
>  此接口由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 方法  
 `IDebugApplication110` 接口公开以下方法。  
  
|方法|说明|  
|--------|--------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|在主线程进行同步调用。|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|在主线程进行异步调用。|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|等待任何指定的句柄信号，则允许跨线程调用时发送到该线程。  必须从调试器线程调用此方法。|