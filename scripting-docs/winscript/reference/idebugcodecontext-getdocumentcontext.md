---
title: "IDebugCodeContext::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::GetDocumentContext"
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::GetDocumentContext
返回文档上下文与此代码上下文。  
  
## 语法  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### 参数  
 `ppsc`  
 \[in\]文档上下文与此代码上下文。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 为文本文档，字符位置范围应该包括整个语句的文本。  这允许调试器IDE显示当前源语句。  
  
## 请参阅  
 [IDebugCodeContext 接口](../../winscript/reference/idebugcodecontext-interface.md)