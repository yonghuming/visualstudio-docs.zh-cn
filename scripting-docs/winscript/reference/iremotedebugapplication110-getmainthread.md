---
title: "IRemoteDebugApplication110::GetMainThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::GetMainThread"
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IRemoteDebugApplication110::GetMainThread
返回中调用的宿主的 [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)主线程;否则返回E\_FAIL。  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md) 由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
  
```  
  
#### 参数  
 `ppThread`  
 \[in\]主 [IRemoteDebugApplicationThread 接口](../../winscript/reference/iremotedebugapplicationthread-interface.md)。  
  
## 请参阅  
 [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 接口](../../winscript/reference/iremotedebugapplication110-interface.md)