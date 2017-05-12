---
title: "IDebugStackFrame::GetLanguageString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetLanguageString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetLanguageString"
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetLanguageString
返回该语言的简短或长的文本说明。  
  
## 语法  
  
```  
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### 参数  
 `fLong`  
 \[in\]标志，`TRUE` 返回一个长说明和 `FALSE` 返回一个简短说明。  
  
 `pbstrLanguage`  
 \[in\]语言的说明。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 通常，因此，如果 `fLong` 是 `FALSE`，此方法提供该语言的名称与堆栈帧。  当 `fLong` 是 `TRUE`时，此方法可以提供完整产品说明。  
  
## 请参阅  
 [IDebugStackFrame 接口](../../winscript/reference/idebugstackframe-interface.md)