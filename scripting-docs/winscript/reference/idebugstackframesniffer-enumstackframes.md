---
title: "IDebugStackFrameSniffer::EnumStackFrames | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrameSniffer.EnumStackFrames
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrameSniffer::EnumStackFrames"
ms.assetid: a7629ab3-ef7d-4bbe-a137-bb2a8ad0f384
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSniffer::EnumStackFrames
返回堆栈帧的枚举数当前线程的。  
  
## 语法  
  
```  
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### 参数  
 `ppedsf`  
 \[in\]堆栈帧的枚举数当前线程的。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 堆栈帧枚举数返回启动位于堆栈顶部的框架，从最近驱动器的帧开始。  
  
## 请参阅  
 [IDebugStackFrameSniffer 接口](../../winscript/reference/idebugstackframesniffer-interface.md)