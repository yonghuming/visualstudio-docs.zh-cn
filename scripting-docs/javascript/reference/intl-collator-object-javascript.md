---
title: "Intl.Collator 对象 (JavaScript) | Microsoft Docs"
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
  - "Collator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Intl.Collator 对象 (JavaScript)
提供特定区域设置的字符串比较。  
  
## 语法  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### 参数  
 `collatorObj`  
 必需。  要向其分配 `Collator` 对象的变量名。  
  
 `locales`  
 可选。  包含一种或多种语言或区域设置标记的区域设置字符串数组。  如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域位置。  如果省略此参数，则使用 JavaScript 运行时的默认区域设置。  有关更多信息，请参见备注部分。  
  
 `options`  
 可选。  包含一个或多个指定比较选项的特性的对象。  有关详细信息，请参见“备注”部分。  
  
## 备注  
 `locales` 参数必须符合 [BCP 47](http://tools.ietf.org/html/rfc5646) 语言或“en\-US”和“zh\-Hans\-CN”等区域设置标记。  标记可能包括语言、区域、国家\/地区和变量。  有关语言列表，请参见[IANA language subtag registry](http://go.microsoft.com/fwlink/p/?linkid=227303)（IANA 语言子标签注册表）。  有关语言标记的示例，请参见 BCP 47 的 [Appendix A](http://tools.ietf.org/html/rfc5646#appendix-A)（附录 A）。  对于 `Collator`，您可能需在区域设置字符串中包含 \- u 扩展名以指定一个或多个以下 Unicode 扩展：  
  
-   \-co 指定不同的排序规则（特定于区域设置）：“*language*\-*region*\-u\-co\-*value*”。  
  
-   \-kn 指定数字比较："*language*\-*region*\-u\-kn\-true&#124;false"。  
  
-   –kf 指定是否首先对大写或小写字符排序："*language*\-*region*\-u\-kf\-upper&#124;lower&#124;false"\)。  目前不支持此扩展。  
  
 要指定一个数值比较，你可以在区域设置字符串中设置 –kn 扩展，或在 `options` 参数中使用 `numeric` 属性。  如果正在使用 `numeric` 属性，–kn 值将不适用。  
  
 `options` 参数可能包括以下属性：  
  
-   `localeMatcher`.  指定要使用的区域设置匹配算法。  可能的值为“lookup”和“best fit”。  默认值为“best fit”。  
  
-   `usage`.  指定比较的目标为排序还是搜索。  可能的值为“sort”和“search”。  默认值为“sort”。  
  
-   `sensitivity`.  指定排序程序的敏感度。  可能的值为“base”、“accent”、“case”和“variant”。  默认值为 `undefined`。  
  
-   `ignorePunctuation`.  指定比较时是否忽略标点符号。  可能的返回值为“true”和“false”。  默认值为 `false`。  
  
-   `numeric`.  指定是否使用数字排序。  可能的返回值为“true”和“false”。  默认值为 `false`。  
  
-   `caseFirst`.  当前不支持。  
  
## 属性  
 下表列出了 `Collator` 对象的属性。  
  
|||  
|-|-|  
|Property|描述|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|返回利用排序程序的排序次序比较两个字符串的函数。|  
|[构造函数](../../javascript/reference/constructor-property-intl-collator.md)|指定创建排序程序的函数。|  
|[Prototype — 原型](../../javascript/reference/prototype-property-intl-collator.md)|为排序程序返回对原型的引用。|  
  
## 方法  
 下表列出了 `Collator` 对象的方法。  
  
|||  
|-|-|  
|方法|描述|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|返回包含排序程序属性和值的对象。|  
  
## 示例  
 下面的示例会创建一个 `Collator` 对象并执行比较。  
  
```javascript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## 示例  
 下面的示例使用 `Collator` 对象对数组排序。  此示例演示了特定于区域设置的差异。  
  
```javascript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## 示例  
 下面的示例使用 `Collator` 对象搜索字符串并指定比较选项。  
  
```javascript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [localeCompare 方法 \(String\)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.DateTimeFormat 对象](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Intl.NumberFormat 对象](../../javascript/reference/intl-numberformat-object-javascript.md)