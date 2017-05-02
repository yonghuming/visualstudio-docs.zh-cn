---
title: "IDebugSyncOperation::InProgressAbort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.InProgressAbort
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::InProgressAbort"
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::InProgressAbort
取消操作正在进行中的另一个线程。  
  
## 语法  
  
```  
HRESULT InProgressAbort();  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|操作无法撤消。|  
|`E_ABORT`|未能完成操作。|  
  
## 备注  
 进程内调试管理器调用此方法从调试器线程内取消正在进行其他线程的操作。  
  
 如果 `InProgressAbort` 方法无法完成操作，则尽快返回 `E_ABORT`。  ;如果操作不能撤消，此方法会返回 `E_NOTIMPL`。  
  
## 请参阅  
 [IDebugSyncOperation 接口](../../winscript/reference/idebugsyncoperation-interface.md)