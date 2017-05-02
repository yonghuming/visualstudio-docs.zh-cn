---
title: "JsRunScript 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsRunScript"
helpviewer_keywords: 
  - "JsRunScript 函数"
ms.assetid: 8d6b8c9a-af3a-4e21-a330-5a6b535423a3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsRunScript 函数
执行脚本。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsRunScript(  
   _In_z_ const wchar_t *script,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### 参数  
 `script`  
 要运行的脚本。  
  
 `sourceContext`  
 一个标识脚本的 Cookie，它可由可调试的脚本上下文使用。  
  
 `sourceUrl`  
 该脚本的来源位置。  
  
 `result`  
 脚本的结果（如果有）。  此参数可以为 null。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)