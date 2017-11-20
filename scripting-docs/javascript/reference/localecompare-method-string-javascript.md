---
title: "localeCompare 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: localeCompare
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: localeCompare method
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056a440d26c4ebf48bd762968fa32ea1efdfb443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="localecompare-method-string-javascript"></a>localeCompare 方法 (String) (JavaScript)
确定两个字符串在当前区域设置是否相等。  
  
## <a name="syntax"></a>语法  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## <a name="parameters"></a>参数  
 `stringVar`  
 必需。 要比较的第一个字符串。  
  
 `stringExp`  
 必需。 要比较的第二个字符串。  
  
 `locales`  
 可选。 包含一种或多种语言或区域设置标记的区域设置字符串数组。 如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域设置。 如果省略此参数，则使用 JavaScript 运行时的默认区域设置。 此参数必须符合[BCP 47](http://tools.ietf.org/html/rfc5646)标准，请参阅[Intl.Collator 对象](../../javascript/reference/intl-collator-object-javascript.md)有关详细信息。  
  
 `options`  
 可选。 包含指定比较选项的一个或多个属性的对象。 请参阅[Intl.Collator 对象](../../javascript/reference/intl-collator-object-javascript.md)有关详细信息。  
  
## <a name="remarks"></a>备注  
 比较字符串中，你可能指定`String`对象或字符串文本。  
  
 在 Internet Explorer 11 中，启动`localeCompare`使用`Intl.Collator`对象内部来进行比较，这增加了对支持`locales`和`options`参数。 有关这些参数的详细信息，请参阅[Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)和[Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md)。  
  
> [!IMPORTANT]
>  不是所有文档模式和浏览器版本中都支持 `locales` 和 `options` 参数。 有关详细信息，请参阅“需求”一节。  
  
 `localeCompare`方法执行区分区域设置的字符串比较的`stringVar`和`stringExp`并返回结果以下项之一，具体取决于系统默认区域设置的排序顺序：  
  
-   -1 如果`stringVar`进行排序之前`stringExp`。  
  
-   + 1 如果`stringVar`后进行排序`stringExp`。  
  
-   0 （零），如果两个字符串相等。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用`localeCompare`。  
  
```JavaScript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用`localeCompare`的德语 （德国） 区域设置。  
  
```JavaScript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`localeCompare`使用德语 （德国） 区域设置和指定德语通讯簿的排序顺序的区域设置特定扩展。 此示例显示了特定于区域设置的差异。  
  
```JavaScript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` 和 `options` 参数：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [toLocaleString 方法 (Object)](../../javascript/reference/tolocalestring-method-object-javascript.md)