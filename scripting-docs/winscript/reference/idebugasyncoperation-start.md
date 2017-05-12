---
title: "IDebugAsyncOperation::Start | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.Start
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::Start"
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::Start
这使得开始异步操作。  
  
## 语法  
  
```  
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### 参数  
 `padocb`  
 接收此操作的状态事件的回调接口。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_UNEXPECTED`|操作已挂起。|  
  
## 备注  
 此方法在从 `IDebugSyncOperation::GetTargetThread`获得的线程导致 `IDebugSyncOperation::Execute` 异步调用。  只应调用此方法从调试器线程内;否则，它不会返回，直到操作完成。  
  
## 请参阅  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [IDebugAsyncOperation 接口](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)