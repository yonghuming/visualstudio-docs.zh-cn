---
title: "IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::EnumCodeContextsOfPosition"
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::EnumCodeContextsOfPosition
用于使一个智能宿主委托 `IDebugDocumentContext::EnumCodeContexts`方法。  
  
## 语法  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### 参数  
 `dwSourceContext`  
 \[in\]源上下文所提供 `IActiveScriptParse::ParseScriptText` 或 `IActiveScriptParse::AddScriptlet`的。  
  
 `uCharacterOffset`  
 \[in\]脚本文本字符偏移量相对于启动。  
  
 `uNumChars`  
 \[in\]中的字符数在此上下文中。  
  
 `ppescc`  
 \[in\]代码上下文的枚举数指定的大小。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 智能宿主使用此方法委托 `IDebugDocumentContext::EnumCodeContexts` 方法。  
  
## 请参阅  
 [IActiveScriptDebug 接口](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)