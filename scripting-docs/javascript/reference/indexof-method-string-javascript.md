---
title: "indexOf 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: indexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- indexOf method, string
- string, indexOf method
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecd96acb21f9d7711f9ee00dbf1c1bb70705c0d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-string-javascript"></a>indexOf 方法 (String) (JavaScript)
返回子字符串首次出现的位置。  
  
## <a name="syntax"></a>语法  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## <a name="parameters"></a>参数  
 `strObj`  
 必需。 A`String`对象或字符串文本。  
  
 `subString`  
 必需。 要在字符串中搜索的子字符串  
  
 `startIndex`  
 可选。 用于开始搜索 `String` 对象的索引。 如果省略此参数，则搜索将从字符串的起始处开始。  
  
## <a name="remarks"></a>备注  
 **IndexOf**方法返回中的子字符串的开头`String`对象。 如果未找到子字符串，则返回 -1。  
  
 如果 `startindex` 为负，则 `startindex` 将被视为零。 如果它大于最大索引，则将其视为最大索引。  
  
 搜索将从左向右执行。 否则，此方法等同于**lastIndexOf**。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**indexOf**方法。  
  
```JavaScript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [lastIndexOf 方法 (String)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [滚动、 平移和缩放示例应用](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)