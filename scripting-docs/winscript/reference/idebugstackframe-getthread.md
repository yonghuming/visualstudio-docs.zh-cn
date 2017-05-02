---
title: "IDebugStackFrame::GetThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetThread
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetThread"
ms.assetid: ece24728-a6b2-4b01-a6f0-0a82b15be39b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetThread
返回线程与此堆栈帧。  
  
## 语法  
  
```  
HRESULT GetThread(  
   IDebugApplicationThread**  ppat  
);  
```  
  
#### 参数  
 `ppat`  
 \[in\]线程与此堆栈帧。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回线程与此堆栈帧。  
  
## 请参阅  
 [IDebugStackFrame 接口](../../winscript/reference/idebugstackframe-interface.md)