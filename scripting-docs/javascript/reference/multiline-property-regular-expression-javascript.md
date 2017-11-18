---
title: "multiline 属性 （正则表达式） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: multiline
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: multiline property
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289cb8d8e103d8c4ac1b1ef06714105d21cba743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="multiline-property-regular-expression-javascript"></a>multiline 属性（正则表达式）(JavaScript)
返回一个布尔值，该值指示多行的标志的状态 (**m**) 与正则表达式一起使用。 默认值是**false**。 只读。  
  
## <a name="syntax"></a>语法  
  
```  
  
rgExp.multiline  
```  
  
## <a name="remarks"></a>备注  
 所需`rgExp`自变量是的一个实例`RegExp`对象  
  
 **多行**属性返回**true**如果多行的标志设置为正则表达式，并返回**false**如果它不是。 **多行**属性是**true**如果使用正则表达式对象创建了**m**标志。  
  
 如果**多行**是**false**，"^"匹配字符串末尾的位置的开头的字符串，以及"$"匹配项的位置。 如果**多行**是**true**，"^"匹配以及字符串的开头的位置，如以下"\n"或"\r"和"$"的位置匹配字符串末尾的位置和前面"\n 的位置"或"\r"。  
  
## <a name="example"></a>示例  
 下面的示例演示的行为**多行**属性。 如果将"m"中传递给下面显示的函数，在词"while"将被替换单词"和"。 这是因为使用多行标志设置和换行字符之后的行开始时，发生在词"while"。 多行标志将允许要在多行字符串上执行搜索。  
  
```JavaScript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**:[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [global 属性 （正则表达式）](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [ignoreCase 属性 （正则表达式）](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)