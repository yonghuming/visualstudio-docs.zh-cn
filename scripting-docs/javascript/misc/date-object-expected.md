---
title: "应为 Date 对象 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5006"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 应为 Date 对象
尝试对 `Date` 之外的类型的对象调用 **Date.prototype.toString** 或 **Date.prototype.valueOf** 方法。  此类调用的对象的类型必须为 `Date`。  例如：  
  
```javascript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### 更正此错误  
  
-   仅对 `Date` 类型的对象调用 **Date.prototype.toString** 或 **Date.prototype.valueOf** 方法。  
  
## 请参阅  
 [Date 对象](../../javascript/reference/date-object-javascript.md)   
 [getDate 方法 \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [内部对象](../../javascript/intrinsic-objects-javascript.md)