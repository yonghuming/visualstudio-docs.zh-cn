---
title: "未定义的标识符 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5009"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 8c8000d9-dd14-487e-922d-98430024a0f6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 未定义的标识符
尝试使用 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 编译器无法识别的标识符。  只要使用以下项，就会返回 undefined 值：  
  
-   不存在的变量、  
  
-   已声明但绝不为其赋值的变量、  
  
-   不存在的对象属性。  
  
### 更正此错误  
  
-   用 **var** 语句（像在 `var` x; 中一样）声明变量。  
  
## 请参阅  
 [变量](../../javascript/variables-javascript.md)   
 [变量范围](../../javascript/advanced/variable-scope-javascript.md)