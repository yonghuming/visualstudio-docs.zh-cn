---
title: "compare 属性 (Intl.Collator) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# compare 属性 (Intl.Collator)
返回利用排序程序的排序次序比较两个字符串的函数。  
  
## 语法  
  
```javascript  
collatorObj.compare  
```  
  
#### 参数  
 `collatorObj`  
 必需。  要用于对比的 `Collator` 对象的名称。  
  
## 备注  
 通过使用 `Collator` 对象中指定的选项，`compare` 属性返回的函数采用两个参数（`x` 和 `y`）并返回 `x` 和 `y` 的特定于区域设置的比较结果。  
  
 比较的结果为：  
  
-   \-1，如果 `x` 排在 `y` 之前。  
  
-   0（零），如果 `x` 与 `y` 的排序次序相同。  
  
-   1，如果 `x` 排在 `y` 之后。  
  
## 示例  
 下面的示例会创建一个 `Collator` 对象并执行比较。  
  
```javascript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
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
 下面的示例使用 `Collator` 对象搜索字符串。  
  
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
 [Intl.Collator 对象](../../javascript/reference/intl-collator-object-javascript.md)