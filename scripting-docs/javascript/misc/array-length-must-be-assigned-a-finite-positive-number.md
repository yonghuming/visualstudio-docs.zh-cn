---
title: "必须为数组长度赋予一个有限的正数 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 必须为数组长度赋予一个有限的正数
在设置现有 **Array** 对象的 **length** 属性时，您指定了非正数或零的数组长度。  在向 `Array` 对象的 **length** 属性（为负数或不为数字 \(`NaN`\)）赋值时出现此错误。  请注意，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 会自动将小数转换为整数。  
  
### 更正此错误  
  
-   将一个正整数赋给 length 属性。  除了最大整数值（约 40 亿）外，数组大小没有上限。  下面的示例演示了设置 **Array** 对象的 **length** 属性的正确方式。  
  
    ```javascript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## 请参阅  
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)