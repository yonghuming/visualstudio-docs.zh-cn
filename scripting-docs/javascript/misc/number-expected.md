---
title: "应为 Number | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5001"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b272f51a-97c2-4398-8b46-9cc49a5c0bd6
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 应为 Number
尝试对 **Number** 之外的其他类型的对象调用 **Number.prototype.toString** 或 **Number.prototype.valueOf** 方法。  此类调用的对象的类型必须为 **Number**。  
  
### 更正此错误  
  
-   仅对 **Number** 类型的对象调用 **Number.prototype.toString** 或 **Number.prototype.valueOf** 方法。  
  
## 请参阅  
 [Number 对象](../../javascript/reference/number-object-javascript.md)   
 [number 属性（错误）](../../javascript/reference/number-property-error-javascript.md)