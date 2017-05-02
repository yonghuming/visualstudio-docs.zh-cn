---
title: "应为 Enumerator 对象 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5015"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 应为 Enumerator 对象
还尝试对 `Enumerator` 之外的类型的对象调用 **Enumerator.prototype.atEnd、Enumerator.prototype.item、Enumerator.prototype.moveFirst** 或 **Enumerator.prototype.moveNext** 方法。  此类调用的对象的类型必须为 `Enumerator`。  以下是违反此规则的代码的示例：  
  
```javascript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### 更正此错误  
  
-   仅对 `Enumerator` 类型的对象调用 **Enumerator.prototype.atEnd**、**Enumerator.prototype.item**、**Enumerator.prototype.moveFirst** 或 **Enumerator.prototype.moveNext** 方法。  若要确定您的对象是否为 `Enumerator` 对象，请使用：  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## 请参阅  
 [Enumerator 对象](../../javascript/reference/enumerator-object-javascript.md)