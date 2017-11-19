---
title: "length 属性 (arguments) (JavaScript) |Microsoft 文档"
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
- length property (arguments)
- Length property
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cede75a91244442f5f28ec9f71b7128814bed5d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-arguments-javascript"></a>length 属性 (arguments) (JavaScript)
返回由调用方传递给函数的参数的实际数目。  
  
## <a name="syntax"></a>语法  
  
```  
[function.]arguments.length  
```  
  
## <a name="remarks"></a>备注  
 可选*函数*自变量是当前正在执行名称`Function`对象。  
  
 **长度**属性**参数**通过脚本引擎传递给自变量的实际数目初始化对象`Function`对象在该函数开始执行时。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**长度**属性**参数**对象。 若要全面了解该示例，请将多个参数传递给比预期的 2 的自变量的函数：  
  
```JavaScript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**: [arguments 对象](../../javascript/reference/arguments-object-javascript.md)&#124;[函数对象](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [arguments 属性 （函数）](../../javascript/reference/arguments-property-function-javascript.md)   
 [length 属性 （数组）](../../javascript/reference/length-property-array-javascript.md)   
 [length 属性（字符串）](../../javascript/reference/length-property-string-javascript.md)