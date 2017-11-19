---
title: "test 方法 （正则表达式） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: test
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: test method
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53e2d2c23821cba5149367c7b5a735fa471bf581
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="test-method-regular-expression-javascript"></a>test 方法（正则表达式）(JavaScript)
返回一个布尔值，该值指示搜索字符串中存在一种模式。  
  
## <a name="syntax"></a>语法  
  
```  
  
rgExp.test(str)   
```  
  
## <a name="parameters"></a>参数  
 `rgExp`  
 必需。 实例**正则表达式**包含正则表达式模式和适用标志的对象。  
  
 `str`  
 必需。 要执行搜索的字符串。  
  
## <a name="remarks"></a>备注  
 **测试**方法检查是否模式在字符串中是否存在并返回**true**如果是这样，和**false**否则为。  
  
 全局属性`RegExp`对象不会修改**测试**方法。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**测试**方法。 若要使用此示例中，向函数传递正则表达式模式和一个字符串。 该函数将返回一个字符串，指示该搜索的结果和测试在字符串中的正则表达式模式的匹配项：  
  
```JavaScript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**:[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)   
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)