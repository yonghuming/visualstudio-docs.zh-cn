---
title: "IDebugApplicationThread::QueryIsCurrentThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.QueryIsCurrentThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::QueryIsCurrentThread"
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::QueryIsCurrentThread
确定此线程是否为当前正在运行的线程。  
  
## 语法  
  
```  
HRESULT QueryIsCurrentThread();  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功，并且这是当前正在运行的线程。|  
|`S_FALSE`|这不是当前正在运行的线程。|  
  
## 备注  
 此方法确定此线程是否为当前正在运行的线程。  
  
## 请参阅  
 [IDebugApplicationThread 接口](../../winscript/reference/idebugapplicationthread-interface.md)