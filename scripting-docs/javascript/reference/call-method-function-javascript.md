---
title: "调用方法 (Function) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: call
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: call method
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ef871f85459ad875a747ae79c7c054b30a82e55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="call-method-function-javascript"></a>call 方法 (Function) (JavaScript)
调用的对象，并替换当前对象的另一个对象的方法。  
  
## <a name="syntax"></a>语法  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## <a name="parameters"></a>参数  
 `thisObj`  
 可选。 要用作当前对象的对象。  
  
 `arg1, arg2, , argN`  
 可选。 要传递给方法的参数列表。  
  
## <a name="remarks"></a>备注  
 `call`方法用于代表另一个对象调用方法。 它允许你更改`this`从原始上下文到指定的新对象的函数对象`thisObj`。  
  
 如果`thisObj`未提供，`global`对象用作`thisObj`。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用 `call` 方法。  
  
```JavaScript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [函数对象](../../javascript/reference/function-object-javascript.md)   
 [apply 方法 (Function)](../../javascript/reference/apply-method-function-javascript.md)