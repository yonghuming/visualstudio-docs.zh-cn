---
title: "Intl.NumberFormat 对象 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "NumberFormat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Intl.NumberFormat 对象 (JavaScript)
提供特定区域设置的数字格式。  
  
## 语法  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### 参数  
 `numberFormatObj`  
 必需。  要向其分配 `NumberFormat` 对象的变量名。  
  
 `locales`  
 可选。  包含一种或多种语言或区域设置标记的区域设置字符串数组。  如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域位置。  如果省略此参数，则使用 JavaScript 运行时的默认区域设置。  有关更多信息，请参见备注部分。  
  
 `options`  
 可选。  包含指定数字格式设置选项的一个或多个特性的对象。  有关详细信息，请参见“备注”部分。  
  
## 备注  
 `locales` 参数必须符合 [BCP 47](http://tools.ietf.org/html/rfc5646) 语言或“en\-us”和“zh CN”等区域设置标记。  标记可能包括语言、区域、国家\/地区和变量。  有关语言标记的示例，请参见 BCP 47 的 [Appendix A](http://tools.ietf.org/html/rfc5646#appendix-A)（附录 A）。  对于 `NumberFormat`，您可以添加 **\-u** 子标记（后面是 \-nu）来指定编号系统扩展：  
  
 “*language*\-*region*\-u\-nu\-*numberingsystem*”  
  
 其中 *numberingsystem* 可为以下各项之一：阿拉伯数字、阿拉伯文数字、巴厘数字、孟加拉数字、梵文数字、全角数字、古吉拉特数字、果鲁穆奇数字、汉语数字、高棉数字、坎纳达数字、老挝数字、拉丁数字、林布数字、马拉雅拉姆数字、蒙古数字、缅甸数字、欧迪亚数字、泰米尔数字、泰卢固数字、泰语数字、藏语数字。  
  
 `options` 参数可能包括以下属性：  
  
|Property|描述|可能的值|默认值|  
|--------------|--------|----------|---------|  
|`localeMatcher`|指定要使用的区域设置匹配算法。|“查找”、“最佳”|“最佳”|  
|`style`|指定数字格式样式。|“decimal”、“百分比”、“货币”|“decimal”|  
|`currency`|将 ISO 4217 货币值指定为字母代码。  如果 `style` 设置为“货币”，则此值为必填项。|请参阅 ISO [货币和资金代码清单](http://www.currency-iso.org/en/home/tables/table-a1.html)。|未定义|  
|`currencyDisplay`|指定将货币显示为 ISO 4217 字母货币代码、本地化的货币符号还是本地化的货币名称。  此值仅在 `style` 设置为“货币”时使用。|“代码”、“符号”、“名称”|“符号”|  
|`useGrouping`|指定是否应使用分组分隔符。|“true”、“false”|`true`.|  
|`minimumIntegerDigits`|指定要使用的整数位的最小数。|1 到 21。|21|  
|`minimumFractionDigits`|.  指定要使用的小数位的最小数。|0 到 20。|0|  
|`maximumFractionDigits`|指定要使用的小数位的最大数。|此值的范围从 `minimumFractionDigits` 到 20。|20.|  
|`minimumSignificantDigits`|指定要显示的小数位的最小数。|此值的范围从 1 到 21。|1|  
|`maximumSignificantDigits`|指定要显示的小数位的最大数。|此值的范围从 `minimumSignificantDigits` 到 21。|21|  
  
## 属性  
 下表列出了 `NumberFormat` 对象的属性。  
  
|||  
|-|-|  
|Property|描述|  
|[构造函数](../../javascript/reference/constructor-property-intl-numberformat.md)|指定创建数字格式化程序对象的函数。|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|返回利用数字格式化设置对数字设置格式的函数。|  
|[Prototype — 原型](../../javascript/reference/prototype-property-intl-numberformat.md)|为数字格式化程序返回对原型的引用。|  
  
## 方法  
 下表列出了 `NumberFormat` 对象的方法。  
  
|||  
|-|-|  
|方法|描述|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|返回包含数字格式化程序对象的属性和值的对象。|  
  
## 示例  
 下面的示例用指定的格式设置选项为 en\-US 区域设置创建 `NumberFormat` 对象。  
  
```javascript  
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
  
## 示例  
 下面的示例显示使用多种不同的区域设置和选项的结果。  
  
```javascript  
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
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [toLocaleString \(Number\)](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator 对象](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.DateTimeFormat 对象](../../javascript/reference/intl-datetimeformat-object-javascript.md)