---
title: "apply 方法 (Function) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: apply
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Apply method
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a06a37006937b07214bf5a314d5151c3b658acf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="apply-method-function-javascript"></a>apply 方法 (Function) (JavaScript)
调用函数，并替换指定的对象的`this`函数，以及指定的数组的函数的自变量的值。  
  
## <a name="syntax"></a>语法  
  
```  
apply([thisObj[,argArray]])  
```  
  
## <a name="parameters"></a>参数  
 `thisObj`  
 可选。 对象要用作`this`对象。  
  
 `argArray`  
 可选。 一组自变量传递到函数。  
  
## <a name="remarks"></a>备注  
 如果`argArray`不是有效的对象，然后"对象应"出错时。  
  
 如果既没有`argArray`也不`thisObj`提供了，原始`this`对象用作`thisObj`和未传入任何参数。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用应用方法。  
  
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
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Function 对象](../../javascript/reference/function-object-javascript.md)