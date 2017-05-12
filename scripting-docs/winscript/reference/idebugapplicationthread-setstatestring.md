---
title: "IDebugApplicationThread::SetStateString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.SetStateString
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::SetStateString"
ms.assetid: a59001d5-ea00-4fd0-bb20-0b592d9c795d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::SetStateString
设置线程状态的说明。  
  
## 语法  
  
```  
HRESULT SetStateString(  
   LPCOLESTR  pstrState  
);  
```  
  
#### 参数  
 `pstrState`  
 \[in\]线程状态的说明。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法设置线程状态的说明。  
  
## 请参阅  
 [IDebugApplicationThread 接口](../../winscript/reference/idebugapplicationthread-interface.md)