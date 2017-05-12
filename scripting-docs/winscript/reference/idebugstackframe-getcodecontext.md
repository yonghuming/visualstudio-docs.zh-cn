---
title: "IDebugStackFrame::GetCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetCodeContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetCodeContext"
ms.assetid: 3dd378f3-e4b7-413e-8812-0f6c72952544
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetCodeContext
返回当前代码上下文与堆栈帧。  
  
## 语法  
  
```  
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### 参数  
 `ppcc`  
 \[out\]上下文代码与堆栈帧。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回当前代码上下文与堆栈帧。  
  
## 请参阅  
 [IDebugStackFrame 接口](../../winscript/reference/idebugstackframe-interface.md)