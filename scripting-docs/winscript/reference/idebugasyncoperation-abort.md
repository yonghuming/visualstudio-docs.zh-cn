---
title: "IDebugAsyncOperation::Abort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.Abort
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::Abort"
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::Abort
取消操作。  
  
## 语法  
  
```  
HRESULT Abort();  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|S\_OK|方法成功。|  
|E\_NOTIMPL|操作无法撤消。|  
  
## 备注  
 此方法通常会调用从调试器线程内取消无响应的操作。  此方法使在 `IDebugSyncOperation` 对象的 `InProgressAbort` 方法调用。  
  
## 请参阅  
 [IDebugAsyncOperation 接口](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)