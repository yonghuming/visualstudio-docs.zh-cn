---
title: "异步 Windows 运行时方法中的特殊错误属性 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# 异步 Windows 运行时方法中的特殊错误属性
在 JavaScript 中调试异步 Windows 运行时方法是很困难的，因此可能在调用堆栈中引发深度的错误。  当应用程序在调试模式中运行时，JavaScript `Error` 对象具有显示仅当从异步 Windows 运行时方法中引发的错误的额外的属性。  
  
## 特定错误属性  
 在调试模式下，从失败的 Windows 运行时异步操作生成的错误对象具有以下特殊属性：  
  
-   `asyncOpSource`（对象）获取有关导致生成错误的调用的原始位置的信息。  属性 `asyncOpSource.originatingCall`（字符串）将在用户的代码中显示源自异步操作的位置。  
  
-   asyncOpType（字符串）获取引发该错误的异步操作类型的名称。  
  
 有关同步操作的更多信息，请参见：  
  
-   [How to handle errors with promises](http://msdn.microsoft.com/zh-cn/01d5a901-c4ea-46f6-8005-6d39c32203eb)  
  
-   [疑难解答 Windows 运行时错误](http://msdn.microsoft.com/zh-cn/1ef7d7df-82ac-441d-8ad0-54ab1318de64)