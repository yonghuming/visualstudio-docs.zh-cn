---
title: "IEnumDebugApplicationNodes::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Skip
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Skip"
ms.assetid: b2ad1957-95b5-4c09-9a44-5a765a5308ae
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Skip
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
 [IEnumDebugApplicationNodes 接口](../../winscript/reference/ienumdebugapplicationnodes-interface.md)