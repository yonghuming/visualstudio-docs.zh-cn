---
title: "IActiveScriptErrorDebug::GetStackFrame | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptErrorDebug.GetStackFrame
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptErrorDebug::GetStackFrame"
ms.assetid: a6f43102-68c5-46f5-a4df-fa3aaf53a967
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug::GetStackFrame
提供实际上是对运行时错误的堆栈帧。  
  
## 语法  
  
```  
HRESULT GetStackFrame(  
   IDebugStackFrame**  ppdsf  
);  
```  
  
#### 参数  
 `ppdsf`  
 \[in\]错误的堆栈帧。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法提供实际上是对运行时错误的堆栈帧。  
  
## 请参阅  
 [IActiveScriptErrorDebug 接口](../../winscript/reference/iactivescripterrordebug-interface.md)