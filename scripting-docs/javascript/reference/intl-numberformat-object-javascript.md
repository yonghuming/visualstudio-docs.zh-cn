---
title: "Intl.NumberFormat 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: NumberFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dcb02dbe0d7a7eef88750c440a4fbcdde3ea7ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="intlnumberformat-object-javascript"></a>Intl.NumberFormat 对象 (JavaScript)
提供区域设置特定的数字格式化。  
  
## <a name="syntax"></a>语法  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>参数  
 `numberFormatObj`  
 必需。 将 `NumberFormat` 对象分配到的变量名。  
  
 `locales`  
 可选。 包含一种或多种语言或区域设置标记的区域设置字符串数组。 如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域设置。 如果省略此参数，则使用 JavaScript 运行时的默认区域设置。 有关详细信息，请参阅备注部分。  
  
 `options`  
 可选。 一个包含一个或多个指定数字的格式设置选项的属性的对象。 有关详细信息，请参见“备注”部分。  
  
## <a name="remarks"></a>备注  
 `locales`参数必须符合[BCP 47](http://tools.ietf.org/html/rfc5646)语言或区域设置标记，例如"EN-US"和"ZH-CN"。 标记可包括语言、区域、国家/地区和变量。 有关语言标记的示例，请参阅[附录 A](http://tools.ietf.org/html/rfc5646#appendix-A)的 BCP 47。 有关`NumberFormat`，您可以添加**-u**子标记后面跟-nu 指定编号系统扩展：  
  
 "*语言*-*区域*-u-nu-*numberingsystem*"  
  
 其中*numberingsystem*可能是下列项之一： 阿拉伯、 arabext、 巴厘、 beng、 deva、 fullwide、 gujr、 专家、 hanidec、 khmr、 knda、 laoo、 latn、 limb、 mylm、 旺、 mymr、 orya、 tamldec、 telu、 泰语、 tibt。  
  
 `options` 参数可包括以下属性：  
  
|属性|描述|可能的值：|默认值|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|指定要使用的区域设置匹配算法。|"lookup"、"best fit"|"best fit"|  
|`style`|指定数字的格式样式。|"decimal"、"百分比"，"货币"|"小数"|  
|`currency`|指定为字母代码组成的 ISO 4217 货币值。 如果`style`设置为"货币"，此值是必需的。|请参阅 ISO[货币和资金代码列表](http://www.currency-iso.org/en/home/tables/table-a1.html)。|undefined|  
|`currencyDisplay`|指定是否显示货币为组成的 ISO 4217 货币字母代码、 本地化的货币符号或本地化的货币名称。 仅当使用此值`style`设置为"货币"。|"代码"、"符号"、"name"|"symbol"|  
|`useGrouping`|指定是否应使用分组分隔符。|true、 false|`true`。|  
|`minimumIntegerDigits`|指定的最小整数位用于数。|1 到 21。|21|  
|`minimumFractionDigits`|. 指定要使用的小数位数的最小数。|0 到 20。|0|  
|`maximumFractionDigits`|指定要使用的小数位数的最大数。|此值可以介于`minimumFractionDigits`为 20。|20.|  
|`minimumSignificantDigits`|指定要显示的小数位数的最小数。|此值可以介于 1 到 21。|1|  
|`maximumSignificantDigits`|指定要显示的小数位数的最大数。|此值可以介于`minimumSignificantDigits`为 21。|21|  
  
## <a name="properties"></a>属性  
 下表列出了 `NumberFormat` 对象的属性。  
  
|||  
|-|-|  
|属性|描述|  
|[构造函数](../../javascript/reference/constructor-property-intl-numberformat.md)|指定创建一个数字的格式化程序对象的函数。|  
|[格式](../../javascript/reference/format-property-intl-numberformat.md)|返回一个函数，设置数字格式使用的数字的格式化程序设置。|  
|[原型](../../javascript/reference/prototype-property-intl-numberformat.md)|返回数字的格式化程序原型的引用。|  
  
## <a name="methods"></a>方法  
 下表列出了 `NumberFormat` 对象的方法。  
  
|||  
|-|-|  
|方法|描述|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|返回包含的属性和值的数字的格式化程序对象的对象。|  
  
## <a name="example"></a>示例  
 下面的示例创建`NumberFormat`对象使用指定的格式设置选项 EN-US 区域设置。  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例演示使用多个不同的区域设置和选项的结果。  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [toLocaleString （数字）](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator 对象](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.DateTimeFormat 对象](../../javascript/reference/intl-datetimeformat-object-javascript.md)