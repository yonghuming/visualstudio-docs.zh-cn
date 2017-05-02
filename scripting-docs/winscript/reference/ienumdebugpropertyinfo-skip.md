---
title: "IEnumDebugPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Skip"
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Skip
跳过 `DebugPropertyInfo` 结构指定数目的枚举序列的。  
  
## 语法  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### 参数  
 `celt`  
 \[in\] `DebugPropertyInfo` 结构数在跳过的枚举序列的。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  返回 `S_FALSE` 并将当前元素指向枚举结束时，如果 `celt` 比在枚举数的元素数大。  
  
## 请参阅  
 [IEnumDebugPropertyInfo 接口](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo 结构](../../winscript/reference/debugpropertyinfo-structure.md)