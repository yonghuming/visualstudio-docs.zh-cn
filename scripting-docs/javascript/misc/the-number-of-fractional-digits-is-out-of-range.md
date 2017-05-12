---
title: "小数位数超出范围 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5026"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dbe05d7d-fcf6-4823-9c61-4b814d1ad3c4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 小数位数超出范围
尝试将无效参数传递给函数 **Number.prototype.toExponential**。  函数 **toExponential\(\)** 的参数必须介于 0 和 20 之间（含 0 和 20）。  
  
### 更正此错误  
  
-   确保 **toExponential\(\)** 的参数不会过大或过小。  
  
## 请参阅  
 [toExponential 方法 \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)