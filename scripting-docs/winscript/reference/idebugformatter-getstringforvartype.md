---
title: "IDebugFormatter::GetStringForVarType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetStringForVarType
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetStringForVarType"
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetStringForVarType
返回表示特定VARTYPE值的字符串。  
  
## 语法  
  
```  
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### 参数  
 `vt`  
 \[in\]表示的VARTYPE作为字符串。  
  
 `ptdescArrayType`  
 \[in\]描述类型的结构数组。  
  
 `pbstr`  
 \[out\]表示 `vt`的字符串。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 方法返回表示特定VARTYPE值的字符串。  
  
## 请参阅  
 [IDebugFormatter 接口](../../winscript/reference/idebugformatter-interface.md)