---
title: "精度超出范围 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5027"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c16760ac-fc08-49d7-8878-9bc434b3c080
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 精度超出范围
尝试将无效参数传递给函数 **Number.prototype.toPrecision**。  **toPrecision** 的参数必须介于 1 和 21 之间（含 1 和 21）。  
  
### 更正此错误  
  
-   确保 `toPrecision` 的参数不会过大或过小。  
  
## 请参阅  
 [toPrecision 方法 \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)