---
title: "JsHasException 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsHasException"
helpviewer_keywords: 
  - "JsHasException 函数"
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsHasException 函数
确定当前上下文的运行时是否处于异常状态。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### 参数  
 `hasException`  
 当前上下文的运行时是否处于异常状态。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 如果调用运行时导致异常（因为运行脚本或因为转换失败等），则运行时将被置于“异常状态”。 在清除该异常前，对运行时创建的任何上下文进行的所有调用（异常 API 除外）都将失败，错误为 `JsErrorInExceptionState`。  
  
 当回调返回到引擎中时，如果当前上下文的运行时处于异常状态，则引擎将自动重新引发异常。  
  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)