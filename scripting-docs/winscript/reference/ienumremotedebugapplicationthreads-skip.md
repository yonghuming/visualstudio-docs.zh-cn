---
title: "IEnumRemoteDebugApplicationThreads::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplicationThreads.Skip
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplicationThreads::Skip"
ms.assetid: bb13a18b-bcf8-4542-8b1a-55a4f2769536
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplicationThreads::Skip
跳过枚举序列中指定数目的段。  
  
## 语法  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### 参数  
 `celt`  
 \[in\]段的数字在跳过的枚举序列的。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法跳过段指定数目的枚举序列的。  
  
## 请参阅  
 [IEnumRemoteDebugApplicationThreads 接口](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)