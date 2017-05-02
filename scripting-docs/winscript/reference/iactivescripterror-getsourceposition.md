---
title: "IActiveScriptError::GetSourcePosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourcePosition"
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourcePosition
检索错误源代码的位置，当脚本引擎运行脚本时。  
  
## 语法  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### 参数  
 `pdwSourceContext`  
 \[in\]接收cookie标识上下文变量的地址。  此参数的解释取决于宿主应用程序。  
  
 `pulLineNumber`  
 \[in\]接收在源文件中的行号该错误变量的地址。  
  
 `pichCharPosition`  
 \[in\]获得行的字符位置该错误变量的地址。  
  
## 返回值  
 返回 `S_OK`，如果成功或 `E_FAIL`，如果此位置未进行检索。  
  
## 请参阅  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)