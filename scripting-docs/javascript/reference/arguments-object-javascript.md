---
title: "arguments 对象 (JavaScript) |Microsoft 文档"
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
- arguments, arguments object
- arguments object
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a5c526d19ad5469d9d099f51cc5a2e2d089814f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-object-javascript"></a>arguments 对象 (JavaScript)
表示指向当前执行函数的自变量和调用它的函数的对象。  
  
## <a name="syntax"></a>语法  
  
```  
[function.]arguments[n]  
```  
  
## <a name="parameters"></a>参数  
 *函数*  
 可选。 当前正在执行的名称`Function`对象。  
  
 *n*  
 必需。 为参数值的从零开始索引传递给`Function`对象。  
  
## <a name="remarks"></a>备注  
 不能显式创建**参数**对象。 **参数**对象仅当将变为可用函数开始执行。 **参数**函数的对象不是数组，但访问相同的方式访问数组元素的各个参数。 索引 *n* 是实际对之一的引用**0**  ***n*** 属性**参数**对象。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**参数**对象。  
  
```JavaScript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [0...n 属性 （参数）](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee 属性 （参数）](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length 属性 (arguments)](../../javascript/reference/length-property-arguments-javascript.md)