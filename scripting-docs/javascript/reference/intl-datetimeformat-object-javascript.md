---
title: "Intl.DateTimeFormat 对象 (JavaScript) | Microsoft Docs"
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
  - "DateTimeFormat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Intl.DateTimeFormat 对象 (JavaScript)
提供特定于区域设置的日期和时间格式。  
  
## 语法  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### 参数  
 `dateTimeFormatObj`  
 必需。  将 `DateTimeFormat` 对象分配到的变量名。  
  
 `locales`  
 可选。  包含一种或多种语言或区域设置标记的区域设置字符串数组。  如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域设置。  如果省略此参数，则使用 JavaScript 运行时的默认区域设置。  有关更多信息，请参见备注部分。  
  
 `options`  
 可选。  包含指定日期和时间格式设置选项的一个或多个特性的对象。  有关详细信息，请参见“备注”部分。  
  
## 备注  
 `locales` 参数必须符合 [BCP 47](http://tools.ietf.org/html/rfc5646) 语言或“en\-us”和“zh\-CN”等区域设置标记。  标记可包括语言、区域、国家\/地区和变量。  有关语言标记的示例，请参见 BCP 47 的[附录 A](http://tools.ietf.org/html/rfc5646#appendix-A)。  对于 `DateTimeFormat`，你可能需在区域设置字符串中添加一个 **\-u** 子标记以包含一个或两个以下 Unicode 扩展：  
  
-   \-nu 指定编号系统扩展：*language*\-*region*\-u\-nu\-*numberingsystem*  
  
     其中 *numberingsystem* 可为以下各项之一：阿拉伯数字、阿拉伯文数字、巴厘数字、孟加拉数字、梵文数字、全角数字、古吉拉特数字、果鲁穆奇数字、汉语数字、高棉数字、坎纳达数字、老挝数字、拉丁数字、林布数字、马拉雅拉姆数字、蒙古数字、缅甸数字、欧迪亚数字、泰米尔数字、泰卢固数字、泰语数字、藏语数字。  
  
-   –ca 指定日历：*language*\-*region*\-u\-ca\-*calendar*  
  
     其中 *calendar* 可为以下各项之一：佛历、农历、公历、回历及和历。  
  
 `options` 参数可包括以下属性：  
  
|属性|说明|可能的值：|默认值|  
|--------|--------|-----------|---------|  
|`localeMatcher`|指定要使用的区域设置匹配算法。|"lookup"、"best fit"|"best fit"|  
|`formatMatcher`|指定要使用的格式匹配算法。|"basic"、"best fit"|"best fit"|  
|`hour12`|指定是否对小时使用 12 小时格式。|`true`（12 小时格式）、`false`（24 小时格式）||  
|`timeZone`|指定时区。  至少 "UTC" 始终受支持。|一个时区值，如 "UTC"。|"UTC"|  
|`weekday`|指定周日期的格式设置。|"narrow"、"short"、"long"。|undefined|  
|`era`|指定纪元的格式设置。|"narrow"、"short"、"long"|undefined|  
|`year`|指定年份的格式设置。|"2\-digit"、"numeric"|undefined 或 "numeric"|  
|`month`|指定月份的格式设置。|"2\-digit"、"numeric"、"narrow"、"short"、"long"|undefined 或 "numeric"|  
|`day`|指定日的格式设置。|"2\-digit"、"numeric"|undefined 或 "numeric"|  
|`hour`|指定小时的格式设置。|"2\-digit"、"numeric"|undefined|  
|`minute`|指定分钟的格式设置。|"2\-digit"、"numeric"|undefined|  
|`second`|指定秒的格式设置。|"2\-digit"、"numeric"|undefined|  
|`timeZoneName`|指定时区的格式设置。  目前不支持此属性。|"short"、"long"。|目前不支持此属性。|  
  
 `weekday`、`era`、`year`、`month`、`day`、`hour`、`minute` 和 `second` 的默认值为 `undefined`。  如果不设置这些属性，则 `year`、`month` 和 `day` 使用 "numeric" 格式。  
  
 每个区域设置必须至少支持以下格式：  
  
-   周日期、年、月、日、小时、分钟、秒  
  
-   周日期、年、月、日  
  
-   年、月、日  
  
-   年、月  
  
-   月、日  
  
-   小时、分钟、秒  
  
-   小时、分钟  
  
## 属性  
 下表列出了 `DateTimeFormat` 对象的属性。  
  
|||  
|-|-|  
|属性|说明|  
|[构造函数](../../javascript/reference/constructor-property-intl-datetimeformat.md)|指定创建日期\/时间格式化程序对象的函数。|  
|[format](../../javascript/reference/format-property-intl-datetimeformat.md)|返回利用日期\/时间格式化程序设置对特定于区域设置的日期设置格式的函数。|  
|[原型](../../javascript/reference/prototype-property-intl-datetimeformat.md)|返回对日期\/时间格式化程序原型的引用。|  
  
## 方法  
 下表列出了 `DateTimeFormat` 对象的方法。  
  
|||  
|-|-|  
|方法|说明|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|返回包含日期\/时间格式化程序对象的属性和值的对象。|  
  
## 示例  
 以下示例演示使用不同的区域设置将日期对象传递给 `DateTimeFormat` 的结果。  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
if (console && console.log) {  
    console.log(new Intl.DateTimeFormat("en-US").format(date));  
    // Returns ‎2‎/‎1‎/‎2013  
    console.log(new Intl.DateTimeFormat("ja-JP").format(date));  
    // Returns ‎2013‎年‎2‎月‎1‎日  
    console.log(new Intl.DateTimeFormat("ar-SA", options).format(date));  
    // Returns ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
    console.log(new Intl.DateTimeFormat("hi-IN", options).format(date));  
    // Returns ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
}  
```  
  
## 示例  
 以下示例将创建一个 `DateTimeFormat` 对象，它会指定当前周日期采用长格式并使用阿拉伯语（沙特阿拉伯）区域设置、回历和拉丁语数字系统。  
  
```javascript  
var dtf = new Intl.DateTimeFormat(["ar-SA-u-ca-islamic-nu-latn"], {  
    weekday: "long",  
    year: "numeric",  
    day: "numeric",  
    month: "long"  
});   
  
If (console && console.log) {  
    console.log(dtf.format(new Date()));  
    // Returns ‏الجمعة‏, ‏19‏ ‏رمضان‏, ‏1434  
}  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [toLocaleString \(Date\)](../../javascript/reference/tolocalestring-date.md)   
 [toLocaleDateString 方法 \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [toLocaleTimeString 方法 \(Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Intl.Collator 对象](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.NumberFormat 对象](../../javascript/reference/intl-numberformat-object-javascript.md)