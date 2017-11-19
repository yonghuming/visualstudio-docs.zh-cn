---
title: "缺少函数 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa2db3e95d4baece288c9f984a7a9cf7a82c9d1d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="function-expected"></a>缺少函数
要么你尝试调用之一**函数原型**不是对象上的方法`Function`对象，或你在函数调用上下文中使用对象。 例如，下面的代码生成此错误，因为**示例**不是函数。  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   只能调用**函数原型**方法`Function`对象。  
  
-   确保你使用的函数调用运算符`()`调用仅函数。  
  
## <a name="see-also"></a>另请参阅  
 [函数对象](../../javascript/reference/function-object-javascript.md)   
 [prototype 属性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)