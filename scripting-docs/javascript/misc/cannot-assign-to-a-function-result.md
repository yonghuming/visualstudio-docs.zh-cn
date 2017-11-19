---
title: "无法给函数结果赋值 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e7ea718aa97ab7b2eb0924458826cd1eac5672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-a-function-result"></a>无法给函数结果赋值
你试图将值分配给函数结果。 函数的结果可以分配给一个变量，但不能用作变量。 如果你想要将新值分配给该函数本身，则省略括号 （函数调用运算符）。 下面的示例演示的情况下，会生成此错误。  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   不要将函数调用结果的值用作内容可以*将分配给*。 您可以将函数调用的结果的分配*给一个变量*尽管。  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   或者，可以将该函数本身 （而不是其返回值） 分配给变量。  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [函数对象](../../javascript/reference/function-object-javascript.md)   
 [编写 JavaScript 代码](../../javascript/writing-javascript-code.md)   
 [函数](../../javascript/functions-javascript.md)