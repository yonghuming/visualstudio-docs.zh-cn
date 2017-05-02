---
title: "IEnumDebugPropertyInfo::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Clone"
ms.assetid: ba6bdfdb-4c12-475c-bafc-efa6c109d7ee
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Clone
创建与当前枚举器包含相同枚举状态的一个枚举器。  
  
## 语法  
  
```  
HRESULT Clone (  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### 参数  
 `ppEnum`  
 \[out\] 返回克隆的 `IEnumDebugPropertyInfo` 接口。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  
  
## 请参阅  
 [IEnumDebugPropertyInfo 接口](../../winscript/reference/ienumdebugpropertyinfo-interface.md)