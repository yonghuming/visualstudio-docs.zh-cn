---
title: "IRemoteDebugApplicationThread::EnumStackFrames | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.EnumStackFrames
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::EnumStackFrames"
ms.assetid: 605ce83d-43d2-47ea-b066-ec8f0da50ca6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::EnumStackFrames
返回堆栈帧的枚举数与该线程。  
  
## 语法  
  
```  
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### 参数  
 `ppedsf`  
 \[in\]堆栈帧的枚举数与该线程。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 必须调用此方法从断点的内部。  堆栈帧枚举数应返回启动位于堆栈顶部的框架，从最近驱动器的帧开始。  
  
## 请参阅  
 [IRemoteDebugApplicationThread 接口](../../winscript/reference/iremotedebugapplicationthread-interface.md)