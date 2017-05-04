---
title: "IDebugPropertyEnumType_All::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugPropertyEnumType_All.GetName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugPropertyEnumType_All::GetName"
ms.assetid: 24bbe4d5-4263-48d0-8e8d-bff957ffcad2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPropertyEnumType_All::GetName
返回包含 `EnumType`的名称BSTR。  
  
## 语法  
  
```  
HRESULT GetName(  
   BSTR*  pname  
);  
```  
  
#### 参数  
 `pname`  
 \[in\]包含 `EnumType`的名称A BSTR。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  
  
## 请参阅  
 [IDebugPropertyEnumType\_All 接口](../../winscript/reference/idebugpropertyenumtype-all-interface.md)