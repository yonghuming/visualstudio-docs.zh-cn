---
title: "global 属性 （正则表达式） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Global
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: global property
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e2b0256fea60b7ab998c504e79565fc7028cd98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="global-property-regular-expression-javascript"></a>global 属性（正则表达式）(JavaScript)
返回一个布尔值，该值指示全局标志的状态 (**g**) 与正则表达式一起使用。 默认值是**false**。 只读。  
  
## <a name="syntax"></a>语法  
  
```  
  
rgExp.global  
```  
  
## <a name="remarks"></a>备注  
 所需`rgExp`引用是的一个实例**正则表达式**对象。  
  
 `global`属性返回**true**如果全局标志的正则表达式，设置，并返回**false**如果它不是。  
  
 全局标志，在使用时，指示搜索应找到在搜索的字符串中，而不仅仅是第一个模式的所有匹配项。 这也称为是全局匹配。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`global`属性。 如果你通过**g**中对函数，如下所示的单词的所有实例"the"都将替换单词"a"。 请注意，"The"开头的字符串都不能替代因为**我**（忽略大小写） 标志不传递给函数。  
  
 此函数将显示与允许的正则表达式标志，它们是关联的属性的条件**g**，**我**，和**m**。 函数也进行了所有替换显示的字符串。  
  
```JavaScript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>示例  
 以下是生成的输出。  
  
```JavaScript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**:[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [ignoreCase 属性 （正则表达式）](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [multiline 属性 （正则表达式）](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)