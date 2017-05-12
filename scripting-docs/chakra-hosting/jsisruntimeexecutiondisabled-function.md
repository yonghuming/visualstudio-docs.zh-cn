---
title: "JsIsRuntimeExecutionDisabled 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsRuntimeExecutionDisabled"
helpviewer_keywords: 
  - "JsIsRuntimeExecutionDisabled 函数"
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsIsRuntimeExecutionDisabled 函数
返回一个值，指示运行时中是否禁止执行脚本。  
  
## 语法  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(  
    _In_ JsRuntimeHandle runtime,  
    _Out_ bool *isDisabled  
);  
```  
  
#### 参数  
 `runtime`  
 指定禁止执行时要检查的运行时。  
  
 `isDisabled`  
 如果禁止执行，则为 `true`；否则为 `false`。  
  
## 返回值  
 如果操作成功，则为 `JsNoError`；否则为失败代码。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)