---
title: "format 属性 (Intl.DateTimeFormat) | Microsoft Docs"
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format 属性 (Intl.DateTimeFormat)
返回利用指定日期\/时间格式化设置对特定区域设置日期设置格式的函数。  
  
## 语法  
  
```  
dateTimeFormatObj.format  
```  
  
#### 参数  
 `dateTimeFormatObj`  
 必需。  要用作格式化程序的 `DateTimeFormat` 对象的名称。  
  
## 备注  
 通过使用 `DateTimeFormat` 对象中指定的选项，`format` 属性返回的函数采用单个参数（`date`）并返回表示经过本地化的日期的字符串。  该返回函数的 `date` 参数必须是数字、日期字符串或 `Date` 对象。  如果未提供 `date`，则函数将使用 [Date.now](../../javascript/reference/date-now-function-javascript.md) 作为默认输入值。  
  
## 示例  
 下面的示例使用 `DateTimeFormat` 对象将日期“2007 年 12 月 1 日”本地化为德语并重新设置其格式。  
  
```javascript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [Intl.DateTimeFormat 对象](../../javascript/reference/intl-datetimeformat-object-javascript.md)