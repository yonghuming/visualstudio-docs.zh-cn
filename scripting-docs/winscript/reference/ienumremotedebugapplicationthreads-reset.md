---
title: "IEnumRemoteDebugApplicationThreads::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplicationThreads.Reset
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplicationThreads::Reset"
ms.assetid: a6ad8a01-4cc0-4f9c-9cfe-c7448c753473
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplicationThreads::Reset
将枚举序列重置到开始处。  
  
## 语法  
  
```  
HRESULT Reset();  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法重置枚举序列与开头。  
  
## 请参阅  
 [IEnumRemoteDebugApplicationThreads 接口](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)