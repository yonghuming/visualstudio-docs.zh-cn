---
title: "应为 String | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5005"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4c214c4b-9cd7-473b-8d90-2344c0375c25
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 应为 String
尝试对 `String` 之外的其他类型的对象调用 **String.prototype.toString** 或 **String.prototype.valueOf** 方法。  此类调用的对象的类型必须为 `String`。  
  
### 更正此错误  
  
-   仅对类型为 `String` 的对象调用 **String.prototype.toString** 或 **String.prototype.valueOf** 方法。  
  
## 请参阅  
 [String 对象](../../javascript/reference/string-object-javascript.md)   
 [toString 方法 \(Object\)](../../javascript/reference/tostring-method-object-javascript.md)