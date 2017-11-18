---
title: "0...n 属性 (arguments) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: 0...n
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: 0...n properties
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f46c7dafef1cdc27d27f619936349637af172740
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="0n-properties-arguments-javascript"></a>0...n 属性（参数）(JavaScript)
返回从各个自变量的实际值**参数**返回对象**参数**正在执行的函数的属性。  
  
## <a name="syntax"></a>语法  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## <a name="parameters"></a>参数  
 *函数*  
 可选。 当前正在执行的名称`Function`对象。  
  
 0、 1、 2、 *、 n*  
 必需。 非负整数，范围在 0 到 *n* 其中 0 表示第一个自变量和 *n* 表示最后一个参数。 最后一个参数的值 *n* 是**arguments.length 1**。  
  
## <a name="remarks"></a>备注  
 返回 0 的值。 。 。 n 的属性是正在执行的函数传递的实际值。 时实际上并没有参数的数组，各个自变量组成**参数**对象访问相同的方式访问数组元素。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**0...**  ***n***属性的**参数**对象。 若要全面了解该示例，请将一个或多个自变量传递给函数：  
  
```JavaScript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**: [arguments 对象](../../javascript/reference/arguments-object-javascript.md)&#124;[函数对象](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [length 属性 （参数）](../../javascript/reference/length-property-arguments-javascript.md)   
 [length 属性（函数）](../../javascript/reference/length-property-function-javascript.md)