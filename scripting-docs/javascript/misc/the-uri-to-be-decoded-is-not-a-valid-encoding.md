---
title: "要解码的 URI 不是有效编码 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5025"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 要解码的 URI 不是有效编码
您尝试解码格式不正确的 URI（统一资源标识符）。  URI 具有特殊的语法；大多数非字母数字字符必须先进行编码，然后才能在 URI 中使用。  可以使用 `encodeURI` 和 `encodeURIComponent` 方法从常规 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 字符串中创建 URI。  
  
 完整的 URI 由一系列组件和分隔符组成。  常规格式为：  
  
```javascript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 尖括号中的名称表示组件，而“:”、“\/”、“;”和“?”是用作分隔符的保留字符。  
  
### 更正此错误  
  
-   确保您只尝试对有效的 URI 进行解码。  您无法对常规 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 字符串进行解码，因为它们可能包含无效字符。  
  
## 请参阅  
 [decodeURI 函数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函数](../../javascript/reference/decodeuricomponent-function-javascript.md)