---
title: "IActiveScriptSite::OnScriptTerminate | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptTerminate
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptTerminate"
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptTerminate
通知宿主该脚本完成执行。  
  
## 语法  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### 参数  
 `pvarResult`  
 \[in\]包含脚本结果变量的地址或 `NULL`，如果脚本不生成结果。  
  
 `pexcepinfo`  
 \[in\]包含异常信息 `EXCEPINFO` 结构的地址生成了该脚本时停止或 `NULL`，如果异常未生成。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  
  
## 备注  
 在对 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 方法的调用，当SCRIPTSTATE\_INITIALIZED设置了标志，完成之前，脚本引擎调用此方法。  此方法可用于返回完成状态和结果返回给宿主。  请注意许多脚本语言，根据主机上接收的事件，具有由宿主定义的生存期。  在这种情况下，此方法可能不调用。  
  
## 请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)