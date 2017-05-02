---
title: "IDebugSyncOperation::GetTargetThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.GetTargetThread
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::GetTargetThread"
ms.assetid: e6eeeb90-b5ed-4727-8434-fa3186c25013
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::GetTargetThread
返回此同步操作的目标应用程序线程。  
  
## 语法  
  
```  
HRESULT GetTargetThread(  
   IDebugApplicationThread**  ppatTarget  
);  
```  
  
#### 参数  
 `ppatTarget`  
 \[in\]此同步操作的目标应用程序线程。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回此同步操作的目标应用程序线程。  
  
## 请参阅  
 [IDebugSyncOperation 接口](../../winscript/reference/idebugsyncoperation-interface.md)