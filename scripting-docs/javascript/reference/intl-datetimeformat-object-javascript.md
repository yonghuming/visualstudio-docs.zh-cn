---
title: "Intl.DateTimeFormat 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DateTimeFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c50d6d7d939ebe05ce3ff9b434111413803ea40
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="intldatetimeformat-object-javascript"></a>Intl.DateTimeFormat 对象 (JavaScript)
提供特定于区域设置的日期和时间格式。  
  
## <a name="syntax"></a>语法  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>参数  
 `dateTimeFormatObj`  
 必需。 将 `DateTimeFormat` 对象分配到的变量名。  
  
 `locales`  
 可选。 包含一种或多种语言或区域设置标记的区域设置字符串数组。 如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域设置。 如果省略此参数，则使用 JavaScript 运行时的默认区域设置。 有关详细信息，请参阅备注部分。  
  
 `options`  
 可选。 包含指定日期和时间格式设置选项的一个或多个特性的对象。 有关详细信息，请参见“备注”部分。  
  
## <a name="remarks"></a>备注  
 `locales`参数必须符合[BCP 47](http://tools.ietf.org/html/rfc5646)语言或区域设置标记，例如"EN-US"和"ZH-CN"。 标记可包括语言、区域、国家/地区和变量。 有关语言标记的示例，请参阅[附录 A](http://tools.ietf.org/html/rfc5646#appendix-A)的 BCP 47。 有关`DateTimeFormat`，您可以添加**-u**子标记中的区域设置字符串以包含一个或两个以下 Unicode 扩展：  
  
-   -nu 指定编号系统扩展：*语言*-*区域*-u-nu-*numberingsystem*  
  
     其中*numberingsystem*可能是下列项之一： 阿拉伯、 arabext、 巴厘、 beng、 deva、 fullwide、 gujr、 专家、 hanidec、 khmr、 knda、 laoo、 latn、 limb、 mylm、 旺、 mymr、 orya、 tamldec、 telu、 泰语、 tibt。  
  
-   -ca 指定日历：*语言*-*区域*-u-ca-*日历*  
  
     其中*日历*可能是下列项之一： 佛、 中文、 gregory，伊斯兰、 islamicc、 日语。  
  
 `options` 参数可包括以下属性：  
  
|属性|描述|可能的值：|默认值|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|指定要使用的区域设置匹配算法。|"lookup"、"best fit"|"best fit"|  
|`formatMatcher`|指定要使用的格式匹配算法。|"basic"、"best fit"|"best fit"|  
|`hour12`|指定是否对小时使用 12 小时格式。|`true`（12 小时格式）、`false`（24 小时格式）||  
|`timeZone`|指定时区。 至少 "UTC" 始终受支持。|一个时区值，如 "UTC"。|"UTC"|  
|`weekday`|指定周日期的格式设置。|"narrow"、"short"、"long"。|undefined|  
|`era`|指定纪元的格式设置。|"narrow"、"short"、"long"|undefined|  
|`year`|指定年份的格式设置。|"2-digit"、"numeric"|undefined 或 "numeric"|  
|`month`|指定月份的格式设置。|"2-digit"、"numeric"、"narrow"、"short"、"long"|undefined 或 "numeric"|  
|`day`|指定日的格式设置。|"2-digit"、"numeric"|undefined 或 "numeric"|  
|`hour`|指定小时的格式设置。|"2-digit"、"numeric"|undefined|  
|`minute`|指定分钟的格式设置。|"2-digit"、"numeric"|undefined|  
|`second`|指定秒的格式设置。|"2-digit"、"numeric"|undefined|  
|`timeZoneName`|指定时区的格式设置。 目前不支持此属性。|"short"、"long"。|目前不支持此属性。|  
  
 `weekday`、`era`、`year`、`month`、`day`、`hour`、`minute` 和 `second` 的默认值为 `undefined`。 如果不设置这些属性，则 `year`、`month` 和 `day` 使用 "numeric" 格式。  
  
 每个区域设置必须至少支持以下格式：  
  
-   周日期、年、月、日、小时、分钟、秒  
  
-   周日期、年、月、日  
  
-   年、月、日  
  
-   年、月  
  
-   月、日  
  
-   小时、分钟、秒  
  
-   小时、分钟  
  
## <a name="properties"></a>属性  
 下表列出了 `DateTimeFormat` 对象的属性。  
  
|||  
|-|-|  
|属性|描述|  
|[构造函数](../../javascript/reference/constructor-property-intl-datetimeformat.md)|指定创建日期/时间格式化程序对象的函数。|  
|[格式](../../javascript/reference/format-property-intl-datetimeformat.md)|返回利用日期/时间格式化程序设置对特定于区域设置的日期设置格式的函数。|  
|[原型](../../javascript/reference/prototype-property-intl-datetimeformat.md)|返回对日期/时间格式化程序原型的引用。|  
  
## <a name="methods"></a>方法  
 下表列出了 `DateTimeFormat` 对象的方法。  
  
|||  
|-|-|  
|方法|描述|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|返回包含日期/时间格式化程序对象的属性和值的对象。|  
  
## <a name="example"></a>示例  
 以下示例演示使用不同的区域设置将日期对象传递给 `DateTimeFormat` 的结果。  
  
```JavaScript  
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
  
## <a name="example"></a>示例  
 以下示例将创建一个 `DateTimeFormat` 对象，它会指定当前周日期采用长格式并使用阿拉伯语（沙特阿拉伯）区域设置、回历和拉丁语数字系统。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [toLocaleString (Date)](../../javascript/reference/tolocalestring-date.md)   
 [toLocaleDateString 方法 (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [toLocaleTimeString 方法 (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Intl.Collator 对象](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.NumberFormat 对象](../../javascript/reference/intl-numberformat-object-javascript.md)