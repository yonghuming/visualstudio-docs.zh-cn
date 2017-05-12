---
title: "应为 VBArray | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5013"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 应为 VBArray
您提供的对象不是所需的 Visual Basic safeArray。  
  
```  
new VBArray(safeArray);  
```  
  
 VBArray 是只读的且无法直接进行创建。  safeArray 参数是一个 VBArray 值，它在传递到 `VBArray` 构造函数之前必须已获得一个 VBArray 值。  若要获取该值，只能从现有的 ActiveX 或其他对象检索它。  
  
### 更正此错误  
  
-   确保只将 **VBArray** 对象传递给 **VBArray** 构造函数。  
  
## 请参阅  
 [VBArray 对象](../../javascript/reference/vbarray-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)