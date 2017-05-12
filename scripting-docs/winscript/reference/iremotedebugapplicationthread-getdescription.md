---
title: "IRemoteDebugApplicationThread::GetDescription | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetDescription
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetDescription"
ms.assetid: 69842e9e-7c1c-4841-a6b2-31505fe85738
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetDescription
获取此线程声明和状态。  
  
## 语法  
  
```  
HRESULT GetDescription(  
   BSTR*  pbstrDescription,  
   BSTR*  pbstrState  
);  
```  
  
#### 参数  
 `pbstrDescription`  
 \[in\]此线程的说明。  
  
 `pbstrState`  
 \[in\]线程状态的说明。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法获取线程声明和状态。  
  
## 请参阅  
 [IRemoteDebugApplicationThread 接口](../../winscript/reference/iremotedebugapplicationthread-interface.md)