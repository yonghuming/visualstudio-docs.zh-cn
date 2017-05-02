---
title: "IDebugApplication::GetCurrentThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.GetCurrentThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::GetCurrentThread"
ms.assetid: 15128e77-6fc6-42a2-8c04-20e22ef03f29
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::GetCurrentThread
返回线程与当前正在运行的线程。  
  
## 语法  
  
```  
HRESULT GetCurrentThread(  
   IDebugApplicationThread**  pat  
);  
```  
  
#### 参数  
 `pat`  
 \[in\]线程与当前正在运行的线程。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回线程与当前正在运行的线程。  
  
## 请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)