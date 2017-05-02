---
title: "IActiveScriptError::GetExceptionInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetExceptionInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetExceptionInfo"
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetExceptionInfo
检索已发生的错误的信息，这些脚本引擎运行脚本时。  
  
## 语法  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### 参数  
 `pexcepinfo`  
 \[in\]获取错误信息 `EXCEPINFO` 结构的地址。  
  
## 返回值  
 返回 `S_OK`，如果成功或 `E_FAIL`，如果错误。  
  
## 请参阅  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)