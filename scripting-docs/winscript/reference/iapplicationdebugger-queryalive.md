---
title: "IApplicationDebugger::QueryAlive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.QueryAlive
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::QueryAlive"
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::QueryAlive
指示调试器是否具有响应能力。  
  
## 语法  
  
```  
HRESULT QueryAlive();  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法指示调试器是否具有响应能力。  此方法的实现应始终返回 `S_OK`。  
  
 如果调试器进程意外停止，COM返回从排列的代理的错误为调用此方法。  
  
## 请参阅  
 [IApplicationDebugger 接口](../../winscript/reference/iapplicationdebugger-interface.md)