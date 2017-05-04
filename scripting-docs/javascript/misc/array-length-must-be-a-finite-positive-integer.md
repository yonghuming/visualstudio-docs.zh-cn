---
title: "数组长度必须为有限的正整数 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5029"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 数组长度必须为有限的正整数
您调用其参数不是整数（整数包含零以及正整数集）的 **Array** 构造函数。  
  
### 更正此错误  
  
-   仅在创建新的 `Array` 对象时使用正整数。  如果要创建具有非整数的单个元素的数组，可通过两步骤过程实现此目的。  首先，创建包含一个元素的数组，然后将值置于第一个元素中 \(array\[0\]\)。  下面是生成该错误的示例。  
  
    ```javascript  
    var piArray = new Array(3.14159);  
    ```  
  
     下面的示例演示指定具有单个数字元素的数组的正确方式。  
  
    ```javascript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     除了最大整数值（约 40 亿）外，数组大小没有上限。  
  
## 请参阅  
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)