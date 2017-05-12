---
title: "IRemoteDebugApplicationThread::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.SetNextStatement
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::SetNextStatement"
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::SetNextStatement
延续的强制尽可能接近特定代码上下文，在特定框架中。  
  
## 语法  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### 参数  
 `pStackFrame`  
 \[in\]堆栈帧对象。  此参数可以是NULL，表示当前堆栈帧应使用。  
  
 `pCodeContext`  
 \[in\]代码上下文。  此参数可以是NULL，表示当前上下文代码应使用。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法强制继续执行尽可能接近 `pCodeContext`指定的代码上下文，在 `pStackFrame`指定的帧中。  这些参数之一可能是 `NULL`，表示当前帧或上下文。  
  
## 请参阅  
 [IRemoteDebugApplicationThread 接口](../../winscript/reference/iremotedebugapplicationthread-interface.md)