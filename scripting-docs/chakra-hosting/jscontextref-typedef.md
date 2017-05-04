---
title: "JsContextRef Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsContextRef Typedef
对脚本上下文的引用。  
  
## 语法  
  
```  
typedef JsRef JsContextRef;  
```  
  
## 备注  
 每个脚本上下文都包含自己的全局对象，它与其他脚本上下文中的全局对象不同。  
  
 许多 Chakra 托管 API 都需要一个“活动”脚本上下文，可使用 `JsSetCurrentContext` 来设置该上下文。  需要对当前上下文进行设置的 Chakra 托管 API 将在其文档中显式发现该上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)