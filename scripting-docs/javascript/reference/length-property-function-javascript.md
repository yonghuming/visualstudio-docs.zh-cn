---
title: "length 属性 （函数） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Length property
- length property (function)
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fbd0334c18da2c6ef8de8366555d79f791e6855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-function-javascript"></a>length 属性 (Function) (JavaScript)
获取定义的函数的参数数量。  
  
## <a name="syntax"></a>语法  
  
```  
  
functionName.length  
```  
  
## <a name="remarks"></a>备注  
 所需*functionName*是函数的名称。  
  
 **长度**创建函数的实例时，由该函数的定义中的参数的数目的脚本引擎初始化函数属性。  
  
 有很多自变量的值不同的调用函数时，会发生什么情况及其**长度**属性取决于函数。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**长度**属性：  
  
```JavaScript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [arguments 属性 （函数）](../../javascript/reference/arguments-property-function-javascript.md)   
 [length 属性 （数组）](../../javascript/reference/length-property-array-javascript.md)   
 [length 属性（字符串）](../../javascript/reference/length-property-string-javascript.md)