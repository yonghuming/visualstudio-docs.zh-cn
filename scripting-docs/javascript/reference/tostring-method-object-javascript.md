---
title: "toString 方法 (Object) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ToString method
ms.assetid: c4ae9da2-60c9-486f-b00a-9df03fda4a35
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518f988486bb527220884052768e61d099dbd716
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-object-javascript"></a>toString 方法 (Object) (JavaScript)
返回对象的字符串表示形式。  
  
## <a name="syntax"></a>语法  
  
```  
  
objectname.toString([radix])  
```  
  
## <a name="parameters"></a>参数  
 `objectname`  
 必需。 为其查找的字符串表示的对象。  
  
 `radix`  
 可选。 指定用于将数值转换为字符串基数。 此值仅用于数字。  
  
## <a name="remarks"></a>备注  
 **ToString**方法是成员的所有内置[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象。 其行为方式取决于的对象类型：  
  
|对象|行为|  
|------------|--------------|  
|数组|元素的`Array`将转换为字符串。 对生成的字符串进行连接，并用逗号隔开。|  
|Boolean|如果布尔值为**true**，返回"`true`"。 否则，返回"`false`"。|  
|日期|返回的文本表示形式的日期。|  
|错误|返回包含相关联的错误消息的字符串。|  
|函数|返回字符串，以下形式，其中*functionname*是函数的名称其**toString**调用了方法：<br /><br /> `function functionname( ) { [native code] }`|  
|数字|返回文本的数字表示形式。|  
|String|返回的值`String`对象。|  
|默认|返回`"[object objectname]"`，其中`objectname`是对象类型的名称。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**toString**使用基数自变量的方法。 下面显示的返回值是函数的基数转换表。  
  
```JavaScript  
function CreateRadixTable (){  
   var s = "";  
  
   // Create table heading.  
   s += "Hex  Dec  Bin \n";  
  
   for (x = 0; x < 16; x++)  
   {  
      s += "   ";  
  
      // Convert to hexidecimal.  
      s += x.toString(16);  
      s += "     ";  
      if (x < 10) s += "  ";  
  
      // Convert to decimal.  
      s += x.toString(10);  
      s += "     ";  
  
      // Convert to binary.  
      s += x.toString(2);  
      s += "\n";  
   }  
  
   return(s);  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **适用于**:[数组对象](../../javascript/reference/array-object-javascript.md)&#124;[Boolean 对象](../../javascript/reference/boolean-object-javascript.md)&#124;[日期对象](../../javascript/reference/date-object-javascript.md)&#124;[错误对象](../../javascript/reference/error-object-javascript.md)&#124;[函数对象](../../javascript/reference/function-object-javascript.md)&#124;[编号对象](../../javascript/reference/number-object-javascript.md)&#124;[Object 对象](../../javascript/reference/object-object-javascript.md)&#124;[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [function 语句](../../javascript/reference/function-statement-javascript.md)