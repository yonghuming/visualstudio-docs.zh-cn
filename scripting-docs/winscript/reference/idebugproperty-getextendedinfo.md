---
title: "IDebugProperty::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetExtendedInfo"
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetExtendedInfo
扩展属性的信息。  
  
## 语法  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### 参数  
 `cInfos`  
 \[in\]计数扩展的信息对象。  
  
 `rgguidExtendedInfo`  
 \[in\]一个数组 `GUID`s通过，以便扩展的信息多个项目可以同时检索。  
  
 `pExtendedInfo`  
 \[in\]返回可用于检索扩展属性信息的数组 `VARIANT`的。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  
  
## 备注  
 此接口扩展此对象的信息。  API提供用于检索不适用于检索使用 `IDebugProperty::GetPropertyInfo`\)的信息的目的仅存在。  
  
## 请参阅  
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)