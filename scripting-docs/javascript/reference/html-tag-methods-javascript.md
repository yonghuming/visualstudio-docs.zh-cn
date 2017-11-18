---
title: "HTML 标记方法 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- link method [JavaScript]
- blink method [JavaScript]
- fontsize method [JavaScript]
- italics method [JavaScript]
- sup method [JavaScript]
- anchor method [JavaScript]
- fixed method [JavaScript]
- fontcolor method [JavaScript]
- bold method [JavaScript]
- small method [JavaScript]
- HTML Tag methods [JavaScript]
- sub method [JavaScript]
- big method [JavaScript]
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7639bc609d8e9b7e4b212fe67ae40f81487d708e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="html-tag-methods-javascript"></a>HTML 标记方法 (JavaScript)
你可以使用 HTML 标记方法将放置在文本周围的 HTML 元素`String`对象。  
  
## <a name="syntax"></a>语法  
 下表列出的语法和每个 HTML 标记方法的说明。  
  
 在语法列中，`string1`是`String`对象或文本。  
  
 标准列指示[World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/?LinkId=199553) HTML 4 的建议。 "建议"指示 HTML 元素不建议使用改用样式表。  
  
|语法|方法描述|参数说明|标准|  
|------------|------------------------|---------------------------|--------------|  
|`string1`.anchor (`name`)|将具有 NAME 属性放置在文本两侧的 HTML 定位点。|`name`参数是要将放入 HTML 定位点的名称属性文本。||  
|`string1`.big()|将 HTML 放置\<大 > 标记放置在文本两侧。||不建议这样做|  
|`string1`.blink()|将 HTML 放置\<BLINK > 标记放置在文本两侧。 \<BLINK > 标记不支持在 Internet Explorer 中。||不在标准|  
|`string1`.bold()|将 HTML 放置\<B > 标记放置在文本两侧。||不建议这样做|  
|`string1`.fixed()|将 HTML 放置\<TT > 标记放置在文本两侧。||不建议这样做|  
|`string1`.fontcolor (`color`)|将 HTML 放置\<字体 > 标记具有 COLOR 特性放置在文本两侧。|`color`参数是包含一种颜色的预定义的名称的十六进制值的字符串值。 有效的预定义的颜色名称取决于[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]托管浏览器和其版本。|不推荐使用|  
|`string1`.fontsize (`size`)|将 HTML 放置\<字体 > 标记具有 SIZE 特性放置在文本两侧。|`size`参数是一个整数值，指定的文本大小。 有效的整数值取决于[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]托管浏览器和其版本。|不推荐使用|  
|`string1`.italics()|将 HTML 放置\<我 > 标记放置在文本两侧。||不建议这样做|  
|`string1`.link (`href`)|将具有 HREF 属性放置在文本两侧的 HTML 定位点。|`href`参数是要将放入 HTML 定位点的 HREF 属性文本。||  
|`string1`.small()|将 HTML 放置\<小 > 标记放置在文本两侧。||不建议这样做|  
|`string1`.strike()|将 HTML 放置\<STRIKE > 标记放置在文本两侧。||不推荐使用|  
|`string1`.sub()|将 HTML 放置\<子 > 标记放置在文本两侧。|||  
|`string1`.sup()|将 HTML 放置\<SUP > 标记放置在文本两侧。|||  
  
## <a name="remarks"></a>备注  
 执行不进行检查以确定是否 HTML 标记包含已应用于字符串。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 HTML 标记方法。  
  
```JavaScript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [String 对象](../../javascript/reference/string-object-javascript.md)