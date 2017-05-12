---
title: "IDebugExpression::GetResultAsString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsString"
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsString
当字符串和操作的返回值，则返回表达式的计算结果。  
  
## 语法  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### 参数  
 `phrResult`  
 \[in\]操作的返回值。  
  
 `pbstrResult`  
 \[in\]表达式计算的结果。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_PENDING`|操作挂起。|  
  
## 备注  
 此方法返回表达式的计算结果为字符串和操作的 `HRESULT`。  
  
 此方法返回 `S_OK`，并 `phrResult` 返回 `E_ABORT`，如果 `Abort` 中止操作。  
  
## 请参阅  
 [IDebugExpression 接口](../../winscript/reference/idebugexpression-interface.md)