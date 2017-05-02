---
title: "IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.SynchronousCallIntoThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::SynchronousCallIntoThread"
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::SynchronousCallIntoThread
为调用方提供框架运行应用程序线程的代码。  
  
## 语法  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### 参数  
 `pstcb`  
 \[in\]调用的对象。  
  
 `dwParam1`  
 \[in\]传递给 `IDebugThreadCall::ThreadCallHandler` 方法的第一个参数。  
  
 `dwParam2`  
 \[in\]传递给 `IDebugThreadCall::ThreadCallHandler` 方法的第二个参数。  
  
 `dwParam3`  
 \[in\]传递给 `IDebugThreadCall::ThreadCallHandler` 方法的第三个参数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法对于调用方提供框架运行在调试器线程的代码。  语言引擎和宿主通常使用此方法实现自由线程的对象在其单一线程的实现的顶部。  
  
## 请参阅  
 [IDebugApplicationThread 接口](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall 接口](../../winscript/reference/idebugthreadcall-interface.md)