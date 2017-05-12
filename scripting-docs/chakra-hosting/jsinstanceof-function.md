---
title: "JsInstanceOf 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94399a62-b996-4fd2-82ce-1c26e7a4da08
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsInstanceOf 函数
执行 JavaScript“instanceof”运算符测试。  
  
## 语法  
  
```  
JsInstanceOf(   
  _In_ JsValueRef object,  
  _In_ JsValueRef constructor,  
  _Out_ bool *result  
);  
  
```  
  
#### 参数  
 `object`  
 要测试的对象。  
  
 `constructor`  
 要用作测试依据的构造函数。  
  
 `result`  
 “object instanceof constructor”是否为 true。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)