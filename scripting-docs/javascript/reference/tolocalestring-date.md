---
title: "toLocaleString （日期） |Microsoft 文档"
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
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6dc7b1f38f7e57d1c10f7197bb73b13b3545380
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-date"></a>toLocaleString (Date)
通过使用当前或指定区域设置将日期转换为字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>参数  
 `dateObj`  
 必需。 要转换的 `Date` 对象。  
  
 `locales`  
 可选。 包含一种或多种语言或区域设置标记的区域设置字符串数组。 如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域设置。 如果省略此参数，则使用 JavaScript 运行时的默认区域设置。  
  
 `options`  
 可选。 包含指定比较选项的一个或多个属性的对象。  
  
## <a name="remarks"></a>备注  
 在 Internet Explorer 11 中，启动`toLocaleString`使用`Intl.DateTimeFormat`内部到进行比较，增加了对支持`locales`和`options`参数。 有关这些参数的详细信息，请参阅[Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  不是所有文档模式和浏览器版本中都支持 `locales` 和 `options` 参数。 有关详细信息，请参阅“要求”一节。  
  
 当你在 Internet Explorer 10 标准文档模式、较早的文档模式和 Quirks 模式中使用 `toLocaleString` 时：  
  
-   它将返回`String`对象，其中包含在当前区域设置的长默认格式写入日期。  
  
-   对于 1999年公元 1601年和之间的日期，在日期格式为根据用户的控制面板区域设置。  
  
> [!NOTE]
>  如果省略`locales`参数，使用`toLocaleString`只是为了向用户显示结果不应使用它来计算值在一个脚本，因为返回的结果因计算机而异。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `toLocaleString` 方法。  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何将 `toLocaleString` 方法用于指定的区域设置和比较选项。  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` 和 `options` 参数：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [toLocaleDateString 方法 (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)