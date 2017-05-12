---
title: "IRemoteDebugApplicationThread::GetApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetApplication"
ms.assetid: 9446c7f9-cfa2-408f-98c5-64f549783de1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetApplication
返回应用程序对象与该线程。  
  
## 语法  
  
```  
HRESULT GetApplication(  
   IRemoteDebugApplication**  pprda  
);  
```  
  
#### 参数  
 `pprda`  
 \[in\]应用程序对象与该线程。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回应用程序对象与该线程。  
  
## 请参阅  
 [IRemoteDebugApplicationThread 接口](../../winscript/reference/iremotedebugapplicationthread-interface.md)