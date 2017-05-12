---
title: "format 属性 (Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format 属性 (Intl.NumberFormat)
返回利用指定数字格式化设置对特定区域设置数字设置格式的函数。  
  
## 语法  
  
```  
numberFormatObj.format  
```  
  
#### 参数  
 `numberFormatObj`  
 必需。  要用作格式化程序的 `NumberFormat` 对象的名称。  
  
## 备注  
 通过使用 `NumberFormat` 对象中指定的选项，`format` 属性返回的函数采用单个参数（`value`）并返回表示经过本地化的数值的字符串。  如果未提供 `value`，则函数返回 `NaN`（不是数字）。  
  
## 示例  
 下面的示例使用 `NumberFormat` 对象来创建本地化数字。  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [Intl.NumberFormat 对象](../../javascript/reference/intl-numberformat-object-javascript.md)