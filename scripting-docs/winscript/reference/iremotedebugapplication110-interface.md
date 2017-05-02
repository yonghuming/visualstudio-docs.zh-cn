---
title: "IRemoteDebugApplication110 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110 接口"
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IRemoteDebugApplication110 接口
用于提供可以通过脚本调用调试器和托管调用方的新功能。  
  
> [!IMPORTANT]
>  此接口由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 方法  
 `IRemoteDebugApplication110` 接口公开以下方法。  
  
|方法|说明|  
|--------|--------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|调用更新调试器选项。  选项默认为0 \(SDO\_NONE\)。|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|返回当前已启用的设置选项。|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|调用返回的宿主的主线程。|