---
title: "IRemoteDebugApplication110::GetCurrentDebuggerOptions | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::GetCurrentDebuggerOptions"
ms.assetid: a6e9cae1-e8f3-4d62-b133-52e9ca12ba7a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplication110::GetCurrentDebuggerOptions
返回当前已启用的设置选项。  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md) 由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
HRESULT GetCurrentDebuggerOptions([out] enum SCRIPT_DEBUGGER_OPTIONS* pCurrentOptions);  
```  
  
#### 参数  
 `pCurrentOptions`  
 \[in\]当前选项卡。  
  
## 请参阅  
 [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 接口](../../winscript/reference/iremotedebugapplication110-interface.md)