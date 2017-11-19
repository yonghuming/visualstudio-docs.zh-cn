---
title: "arguments 属性 （函数） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments property
- Arguments property
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0b18fb8164639119e5db5e7a5d76b4280f9c9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-property-function-javascript"></a>arguments 属性（函数）(JavaScript)
获取当前正在执行的自变量`Function`对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
function.arguments  
```  
  
## <a name="remarks"></a>备注  
 `function`参数是当前执行函数的名称，可以省略。  
  
 此属性允许函数来处理数目可变的参数。 **长度**属性`arguments`对象包含传递给函数的参数的数目。 中的单个参数`arguments`对象可以访问与访问数组元素的方式相同。  
  
## <a name="example"></a>示例  
 下面的示例演示 `arguments` 属性的用法：  
  
```JavaScript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [arguments 对象](../../javascript/reference/arguments-object-javascript.md)   
 [function 语句](../../javascript/reference/function-statement-javascript.md)