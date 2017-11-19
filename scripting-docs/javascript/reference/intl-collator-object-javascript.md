---
title: "Intl.Collator 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Collator
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9a41507face20285124257be95197ef5ea53ef6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="intlcollator-object-javascript"></a>Intl.Collator 对象 (JavaScript)
提供区域设置特定的字符串比较。  
  
## <a name="syntax"></a>语法  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### <a name="parameters"></a>参数  
 `collatorObj`  
 必需。 将 `Collator` 对象分配到的变量名。  
  
 `locales`  
 可选。 包含一种或多种语言或区域设置标记的区域设置字符串数组。 如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域设置。 如果省略此参数，则使用 JavaScript 运行时的默认区域设置。 有关详细信息，请参阅备注部分。  
  
 `options`  
 可选。 包含指定比较选项的一个或多个属性的对象。 有关详细信息，请参见“备注”部分。  
  
## <a name="remarks"></a>备注  
 `locales`参数必须符合[BCP 47](http://tools.ietf.org/html/rfc5646)语言或区域设置标记，例如"EN-US"和"Hans-ZH-CN"。 标记可包括语言、区域、国家/地区和变量。 有关语言的列表，请参阅[IANA 语言子标记注册表](http://go.microsoft.com/fwlink/p/?linkid=227303)。 有关语言标记的示例，请参阅[附录 A](http://tools.ietf.org/html/rfc5646#appendix-A)的 BCP 47。 有关`Collator`，可能要指定一个或多个以下 Unicode 扩展的区域设置字符串中包括-u 扩展：  
  
-   -共同指定变量的排序规则 （特定于区域设置）:"*语言*-*区域*-u-协*值*"。  
  
-   -kn 指定数值的比较:"*语言*-*区域*-u kn true &#124; 否则为 false"。  
  
-   -kf 以指定是否首先排序大写或小写字符:"*语言*-*区域*-u kf 上限 &#124; 较低 &#124; 否则为 false")。 当前不支持此扩展。  
  
 若要指定数值的比较，你可以在区域设置字符串中设置-kn 扩展，或使用`numeric`中的属性`options`参数。 如果你使用`numeric`属性，将不会应用-kn 值。  
  
 `options` 参数可包括以下属性：  
  
-   `localeMatcher`。 指定要使用的区域设置匹配算法。 可能的值为"查找"和"best fit"。 默认值为"适合"。  
  
-   `usage`。 指定是否比较的目标是排序或搜索。 可能的值为"排序"和"搜索"。 默认值为"排序"。  
  
-   `sensitivity`。 指定排序程序的敏感度。 可能的值为"基本"、"区分重音"、"用例"和"变体"。 默认值为 `undefined`。  
  
-   `ignorePunctuation`。 指定是否在比较中忽略标点。 可能的值为"true"和"false"。 默认值为 `false`。  
  
-   `numeric`。 指定是否使用数值排序。 可能的值为"true"和"false"。 默认值为 `false`。  
  
-   `caseFirst`。 目前尚不支持。  
  
## <a name="properties"></a>属性  
 下表列出了 `Collator` 对象的属性。  
  
|||  
|-|-|  
|属性|描述|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|返回一个函数，通过使用排序程序的排序顺序比较两个字符串。|  
|[构造函数](../../javascript/reference/constructor-property-intl-collator.md)|指定创建排序程序的函数。|  
|[原型](../../javascript/reference/prototype-property-intl-collator.md)|返回排序程序原型的引用。|  
  
## <a name="methods"></a>方法  
 下表列出了 `Collator` 对象的方法。  
  
|||  
|-|-|  
|方法|描述|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|返回一个包含属性和排序程序的值的对象。|  
  
## <a name="example"></a>示例  
 下面的示例创建`Collator`对象，并执行比较。  
  
```JavaScript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## <a name="example"></a>示例  
 下面的示例使用`Collator`要对数组进行排序的对象。 此示例显示了特定于区域设置的差异。  
  
```JavaScript  
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
  
## <a name="example"></a>示例  
 下面的示例使用`Collator`要搜索的字符串对象和指定的比较选项。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [localeCompare 方法 (String)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.DateTimeFormat 对象](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Intl.NumberFormat 对象](../../javascript/reference/intl-numberformat-object-javascript.md)