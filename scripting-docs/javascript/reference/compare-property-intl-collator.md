---
title: "compare 属性 (Intl.Collator) |Microsoft 文档"
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
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bfd222ac8d2c94efe279177e7f4d8ffdf850f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="compare-property-intlcollator"></a>compare 属性 (Intl.Collator)
返回一个函数，通过使用排序程序的排序顺序比较两个字符串。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
collatorObj.compare  
```  
  
#### <a name="parameters"></a>参数  
 `collatorObj`  
 必需。 名称`Collator`要用于比较的对象。  
  
## <a name="remarks"></a>备注  
 返回的函数`compare`属性采用两个参数，`x`和`y`，并返回结果的特定于区域设置比较`x`和`y`通过使用中指定的选项`Collator`对象。  
  
 比较的结果将是：  
  
-   -1 如果`x`早`y`在排序顺序。  
  
-   0 （零） 如果`x`等同于`y`在排序顺序。  
  
-   如果`x`后，将`y`在排序顺序。  
  
## <a name="example"></a>示例  
 下面的示例创建`Collator`对象，并执行比较。  
  
```JavaScript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
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
 下面的示例使用`Collator`要搜索的字符串对象。  
  
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
 [Intl.Collator 对象](../../javascript/reference/intl-collator-object-javascript.md)