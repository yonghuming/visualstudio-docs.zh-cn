---
title: "IEnumDebugExpressionContexts::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExpressionContexts.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugExpressionContexts::Next"
ms.assetid: aa223b0b-f7c1-4368-a59e-677e60133baf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExpressionContexts::Next
检索枚举序列中指定数目的段。  
  
## 语法  
  
```  
HRESULT Next(  
   ULONG                      celt,  
   IDebugExpressionContext**  ppdec,  
   ULONG*                     pceltFetched  
);  
```  
  
#### 参数  
 `celt`  
 \[in\]要检索的段的数目。  
  
 `ppdec`  
 \[in\]返回表示检索的段的数组 `IDebugExpressionContext` 接口。  
  
 `pceltFetched`  
 \[in\]枚举数获取的段的实际数目。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法检索段指定数目的枚举序列的。  
  
## 请参阅  
 [IEnumDebugExpressionContexts 接口](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)