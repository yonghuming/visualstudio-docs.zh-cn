---
title: "IActiveScriptError::GetSourceLineText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourceLineText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourceLineText"
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourceLineText
检索在错误的源文件的行，在一个脚本引擎运行脚本时。  
  
## 语法  
  
```  
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## Parameter  
 `pbstrSourceLine`  
 \[in\]接收源代码行该错误缓冲区的地址。  
  
## 返回值  
 返回 `S_OK`，如果成功或 `E_FAIL`，如果源文件中的行没有检索。  
  
## 请参阅  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)