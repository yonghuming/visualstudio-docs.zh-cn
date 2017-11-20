---
title: "toLocaleString （数字） |Microsoft 文档"
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b5e6378ec94e032c908a3502c0324c2a5a91b26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-number"></a>toLocaleString (Number)
将数字转换为一个字符串，通过当前或指定区域设置。  
  
## <a name="syntax"></a>语法  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>参数  
 `numberObj`  
 必需。 要转换的 `Number` 对象。  
  
 `locales`  
 可选。 包含一种或多种语言或区域设置标记的区域设置字符串数组。 如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域设置。 如果省略此参数，则使用 JavaScript 运行时的默认区域设置。  
  
 `options`  
 可选。 包含指定比较选项的一个或多个属性的对象。  
  
## <a name="remarks"></a>备注  
 在 Internet Explorer 11 中，启动`toLocaleString`使用`Intl.NumberFormat`内部到进行比较，增加了对支持`locales`和`options`参数。 有关这些参数的详细信息，请参阅[Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  不是所有文档模式和浏览器版本中都支持 `locales` 和 `options` 参数。 有关详细信息，请参阅“需求”一节。  
  
> [!NOTE]
>  如果省略`locales`参数，使用`toLocaleString`只是为了向用户显示结果不应使用它来计算值在一个脚本，因为返回的结果是计算机特定 （该方法返回当前区域设置）。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`toLocaleString`不带任何参数的方法。  
  
```JavaScript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何将 `toLocaleString` 方法用于指定的区域设置和比较选项。  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` 和 `options` 参数：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [toLocaleDateString 方法 (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)