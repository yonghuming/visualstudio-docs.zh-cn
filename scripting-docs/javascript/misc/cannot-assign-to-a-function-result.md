---
title: "无法给函数结果赋值 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5003"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 无法给函数结果赋值
尝试为函数结果赋值。  可将函数的结果赋给变量，但不能将它用作变量。  如果要将新值赋给函数本身，请省略小括号（函数调用运算符）。  下面的示例演示生成此错误的情形。  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### 更正此错误  
  
-   不要将函数调用结果的值用作可以“赋值”的对象。  不过，可以将函数调用的结果赋给*变量*。  
  
    ```javascript  
    myVar = myFunction(42);  
    ```  
  
-   或者，可以将函数本身（而不是其返回值）赋给变量。  
  
    ```javascript  
    myFunction = new Function("return 42;");  
    ```  
  
## 请参阅  
 [Function 对象](../../javascript/reference/function-object-javascript.md)   
 [编写 JavaScript 代码](../../javascript/writing-javascript-code.md)   
 [函数](../../javascript/functions-javascript.md)