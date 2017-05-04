---
title: "要编码的 URI 包含无效字符 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5024"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 要编码的 URI 包含无效字符
尝试将字符串编码为 URI（统一资源标识符），但它包含无效字符。  虽然大多数字符在要转换为 URI 的字符串中都是有效的，但某些 Unicode 字符序列是非法的。  
  
### 更正此错误  
  
-   确保要编码的字符串仅包含有效的 Unicode 序列。  完整的 URI 由一系列组件和分隔符组成。  尖括号中的名称表示组件，而“:”、“\/”、“;”和“?”是用作分隔符的保留字符。  常规格式为：  
  
    ```javascript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## 请参阅  
 [encodeURI 函数](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 函数](../../javascript/reference/encodeuricomponent-function-javascript.md)