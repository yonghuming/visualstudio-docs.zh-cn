---
title: "JsStringToPointer 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStringToPointer"
helpviewer_keywords: 
  - "JsStringToPointer 函数"
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsStringToPointer 函数
检索字符串值的字符串指针。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### 参数  
 `value`  
 要转换为字符串指针的字符串值。  
  
 `stringValue`  
 字符串指针。  
  
 `stringLength`  
 字符串的长度。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 此函数可检索字符串值的字符串指针。  如果值的类型不是字符串，则它将失败，错误为 `JsErrorInvalidArgument`。  返回的字符串生存期将与其所源于的值的生存期相同，但字符串指针不会被视为对值的引用（因此不会对其进行收集）。  
  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)