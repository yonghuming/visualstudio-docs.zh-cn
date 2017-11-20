---
title: "在不支持的值参数中的循环引用 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25489065ceece41108a75c9d3763a95e4adb924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="circular-reference-in-value-argument-not-supported"></a>不支持在值自变量中进行循环引用
尝试调用`JSON.stringify`不是有效的值。 `value`参数、 数组或对象，包含循环引用。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   从自变量中删除的循环引用。  
  
## <a name="example"></a>示例  
 此示例中的代码将导致运行时错误，因为`john`具有对引用`mary`和`mary`具有对引用`john`。 若要删除的循环引用，请移除或取消设置该属性`brother`从`mary`对象或`sister`属性从`john`对象。  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>另请参阅  
 [JSON 对象](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 函数](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript 运行时错误](../../javascript/reference/javascript-run-time-errors.md)