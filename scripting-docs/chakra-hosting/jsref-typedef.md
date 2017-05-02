---
title: "JsRef Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRef Typedef
对 Chakra 垃圾回收器所拥有的某个对象的引用。  
  
## 语法  
  
```  
typedef void *JsRef;  
```  
  
## 备注  
 Chakra 运行时将自动跟踪 JsRef 引用，只要它们存储在局部变量或参数中（即  堆栈上）。  如果将 JsRef 存储在除堆栈外的某个位置中，则需要通过调用 JsAddRef 和 JsRelease 来管理该对象的生存期，否则垃圾回收器将释放该对象，即便该对象仍处于使用中也是如此。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)