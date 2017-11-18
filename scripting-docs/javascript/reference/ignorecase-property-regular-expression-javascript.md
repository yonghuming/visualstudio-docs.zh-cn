---
title: "ignoreCase 属性 （正则表达式） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ignoreCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: IgnoreCase property
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae9fee8e6303fb944f59c11c173f9e8b7f7cc75a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ignorecase-property-regular-expression-javascript"></a>ignoreCase 属性（正则表达式）(JavaScript)
返回一个布尔值，该值 ignoreCase 标志的状态 (**我**) 与正则表达式一起使用。 默认值是**false**。 只读。  
  
## <a name="syntax"></a>语法  
  
```  
  
rgExp.ignoreCase  
```  
  
## <a name="remarks"></a>备注  
 所需`rgExp`引用是的一个实例`RegExp`对象。  
  
 **IgnoreCase**属性返回**true**如果 ignoreCase 标志设置为正则表达式，并返回**false**如果它不是。  
  
 IgnoreCase 标志，在使用时，指示与模式匹配的搜索字符串内搜索中应该不区分大小写。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**ignoreCase**属性。 如果将"gi"中传递给下面显示的函数，该单词的所有实例"the"都将替换单词"a"，包括初始"The"。 这是因为 ignoreCase 标志设置，搜索将忽略任何区分大小写。 因此"T"是"t"相同为了匹配。  
  
 此函数将返回布尔值，用于指示是否允许正则表达式标志的状态**g**，**我**，和**m**。 函数还返回进行了所有替换的字符串。  
  
```JavaScript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>示例  
 以下是生成的输出。  
  
```JavaScript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**:[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [global 属性 （正则表达式）](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [multiline 属性 （正则表达式）](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)