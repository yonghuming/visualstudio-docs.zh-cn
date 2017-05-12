---
title: "应为布尔值 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5010"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 应为布尔值
尝试对 `Boolean` 之外的其他类型的对象调用 **Boolean.prototype.toString** 或 **Boolean.prototype.valueOf** 方法。  此类调用的对象的类型必须为 `Boolean`。  例如：  
  
```javascript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### 更正此错误  
  
-   仅对 **Boolean** 类型的对象调用 Boolean**.prototype.toString** 或 **Boolean.prototype.valueOf** 方法。  
  
## 请参阅  
 [Boolean 对象](../../javascript/reference/boolean-object-javascript.md)   
 [数据类型](../../javascript/data-types-javascript.md)   
 [控制程序流](../../javascript/controlling-program-flow-javascript.md)   
 [复制、传递和比较数据](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)