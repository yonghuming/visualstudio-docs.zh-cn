---
title: "应为正则表达式对象 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 应为正则表达式对象
尝试对 `RegExp` 之外的类型的对象调用 **RegExp.prototype.toString** 或 **RegExp.prototype.valueOf** 方法。  此类调用的对象的类型必须为 `RegExp`。  
  
### 更正此错误  
  
-   仅对 `RegExp` 类型的对象调用 **RegExp.prototype.toString** 或 **RegExp.prototype.valueOf** 方法。  
  
## 请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)