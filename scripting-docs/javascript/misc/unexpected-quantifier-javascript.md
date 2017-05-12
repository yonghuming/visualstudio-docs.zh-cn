---
title: "意外的限定符 (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 意外的限定符 (JavaScript)
在构造正则表达式的搜索模式时，使用非法重复因子创建了模式元素。  例如，模式  
  
```  
/^+/  
```  
  
 是非法的，因为元素 ^（输入的开头）不能具有重复因子。  下表列出了不能具有重复因子的元素。  
  
|元素|说明|  
|--------|--------|  
|^|输入的开头|  
|$|输入的结尾|  
|\\b|单词边界|  
|\\B|非字边界|  
|\*|零个或多个重复|  
|\+|一个或多个重复|  
|?|零个或一个重复|  
|{n}|n 个重复|  
|{n,}|n 个或多个重复|  
|{n,m}|从 n 到 m 个重复（含 n 和 m）|  
  
### 更正此错误  
  
-   确保搜索模式元素只包含合法的重复因子。  
  
## 请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)