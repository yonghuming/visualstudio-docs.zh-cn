---
title: "IDebugCodeContext::SetBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.SetBreakPoint
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::SetBreakPoint"
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::SetBreakPoint
此代码上下文设置或清除断点。  
  
## 语法  
  
```  
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### 参数  
 `bps`  
 \[in\]用于此代码上下文指定断点状态。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法在此代码上下文设置或清除断点。  
  
## 请参阅  
 [IDebugCodeContext 接口](../../winscript/reference/idebugcodecontext-interface.md)   
 [BREAKPOINT\_STATE 枚举](../../winscript/reference/breakpoint-state-enumeration.md)