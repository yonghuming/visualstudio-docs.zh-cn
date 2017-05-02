---
title: "IDebugExpressionContext::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext.GetLanguageInfo
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext::GetLanguageInfo"
ms.assetid: 35e25662-0b2a-4c3f-bce4-f01726bc04a8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext::GetLanguageInfo
返回一个名称和GUID拥有此上下文的语言。  
  
## 语法  
  
```  
HRESULT GetLanguageInfo(  
   BSTR*  pbstrLanguageName,  
   GUID*  pLanguageID  
);  
```  
  
#### 参数  
 `pbstrLanguageName`  
 \[in\]语言的名称。  
  
 `pLanguageID`  
 \[in\]语言的唯一ID。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回一个名称和GUID拥有此上下文的语言。  
  
## 请参阅  
 [IDebugExpressionContext 接口](../../winscript/reference/idebugexpressioncontext-interface.md)