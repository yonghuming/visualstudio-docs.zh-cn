---
title: "IDebugStackFrame::GetDescriptionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetDescriptionString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetDescriptionString"
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetDescriptionString
返回堆栈帧的简短或长的文本说明。  
  
## 语法  
  
```  
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### 参数  
 `fLong`  
 \[in\]标志，`TRUE` 返回一个长说明和 `FALSE` 返回一个简短说明。  
  
 `pbstrDescription`  
 \[in\]堆栈帧的说明。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 通常，因此，如果 `fLong` 是 `FALSE`，此方法提供函数的名称与堆栈帧。  当 `fLong` 是 `TRUE`时，此方法还提供函数参数和其他相关信息。  
  
## 请参阅  
 [IDebugStackFrame 接口](../../winscript/reference/idebugstackframe-interface.md)