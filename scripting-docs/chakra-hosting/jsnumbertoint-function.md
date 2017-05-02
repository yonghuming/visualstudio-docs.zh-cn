---
title: "JsNumberToInt 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsNumberToInt 函数
检索数值的 `int` 值。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### 参数  
 `value`  
 将转换为 `int` 值的数值。  
  
 `intValue`  
 `int` 值。  
  
## 返回值  
  
## 备注  
 此函数检索数值的值并转换为 `int` 值。  如果值的类型不是数字，则它将失败，错误为 `JsErrorInvalidArgument`。  
  
 需要活动脚本上下文。  
  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)