---
title: "IRemoteDebugApplicationEvents::OnBreakFlagChange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnBreakFlagChange
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnBreakFlagChange"
ms.assetid: 25684454-a0d8-47e0-85f5-2217069a9f45
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnBreakFlagChange
处理事件，发生重大更改标志。  
  
## 语法  
  
```  
HRESULT OnBreakFlagChange(  
   APPBREAKFLAGS                   abf,  
   IRemoteDebugApplicationThread*  prdatSteppingThread  
);  
```  
  
#### 参数  
 `abf`  
 \[in\]应用程序的当前中断标志。  
  
 `prdatSteppingThread`  
 \[in\]当前正在运行的线程。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法处理事件，发生重大更改标志。  
  
## 请参阅  
 [IRemoteDebugApplicationEvents 接口](../../winscript/reference/iremotedebugapplicationevents-interface.md)   
 [APPBREAKFLAGS 枚举](../../winscript/reference/appbreakflags-enumeration.md)