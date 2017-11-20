---
title: "return 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: return_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- terminating execution
- return statement
- function statement
- return statement, syntax
- return statement, exiting functions in script
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c28f17bed2dfff021ea1aea268bb7a2eb3f3e58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="return-statement-javascript"></a>return 语句 (JavaScript)
从当前函数退出，并从此函数返回一个值。  
  
## <a name="syntax"></a>语法  
  
```  
  
return[(][expression][)];   
```  
  
## <a name="remarks"></a>备注  
 可选*表达式*自变量是要从函数返回的值。 如果省略，则该函数不返回值。  
  
 你使用`return`语句用于停止执行函数并返回的值*表达式*。 如果*表达式*省略，或根本没有`return`从在函数中执行语句时，将调用当前函数的表达式会分配未定义的值。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `return` 语句的用法。  
  
```JavaScript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`return`语句以返回一个函数。  
  
```JavaScript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [function 语句](../../javascript/reference/function-statement-javascript.md)