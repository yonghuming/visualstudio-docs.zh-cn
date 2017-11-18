---
title: "toLocaleDateString 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleDateString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleDateString method
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b4b019ad329a73bec13766932fbcadfa2ed133
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaledatestring-method-date-javascript"></a>toLocaleDateString 方法 (Date) (JavaScript)
返回作为适用于宿主环境的当前区域设置或指定的区域设置的字符串值的日期。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### <a name="parameters"></a>参数  
 `dateObj`  
 必需。 一个 `Date` 对象。  
  
 `locales`  
 可选。 包含一种或多种语言或区域设置标记的区域设置字符串数组。 如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域设置。 如果省略此参数，则使用 JavaScript 运行时的默认区域设置。  
  
 `options`  
 可选。 包含指定比较选项的一个或多个属性的对象。  
  
## <a name="remarks"></a>备注  
 在 Internet Explorer 11 中，启动`toLocaleDateString`使用`Intl.DateTimeFormat`内部，若要设置格式的日期，增加了对支持`locales`和`options`参数。 有关这些参数的详细信息，请参阅[Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  不是所有文档模式和浏览器版本中都支持 `locales` 和 `options` 参数。 有关详细信息，请参阅“要求”一节。  
  
 当你在 Internet Explorer 10 标准文档模式、较早的文档模式和 Quirks 模式中使用 `toLocaleDateString` 时：  
  
-   它将返回一个字符串值，包含在当前时区的日期。  
  
-   返回的日期是宿主环境的当前区域设置的默认格式。  
  
 如果省略 `locales` 参数，此方法的返回值不能依赖于编写脚本，因为它会因计算机的不同而有所变化。 在此方案中，使用该方法仅显示文本的格式-永远不会作为计算的一部分。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将 `toLocaleDateString` 方法用于指定的区域设置和比较选项。  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` 和 `options` 参数：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [toDateString 方法 (Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString 方法 (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)