---
title: "IEnumDebugExtendedPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Skip"
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Skip
跳过 `ExtendedDebugPropertyInfo` 结构指定数目的枚举序列的。  
  
## 语法  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### 参数  
 `celt`  
 \[in\] `ExtendedDebugPropertyInfo` 结构数在跳过的枚举序列的。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  返回 `S_FALSE` 并将当前元素指向枚举结束时，如果 `celt` 比在枚举数的元素数大。  
  
## 请参阅  
 [IEnumDebugExtendedPropertyInfo 接口](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 结构](../../winscript/reference/extendeddebugpropertyinfo-structure.md)