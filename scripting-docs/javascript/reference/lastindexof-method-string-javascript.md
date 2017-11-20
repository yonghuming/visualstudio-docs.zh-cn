---
title: "lastIndexOf 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: lastIndexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndexOf method, string
- string, lastIndexOf method
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fa0f35e970435a4d0296493c20afdeaac128cae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-string-javascript"></a>lastIndexOf 方法 (String) (JavaScript)
返回字符串中子字符串的最后一个匹配项。  
  
## <a name="syntax"></a>语法  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## <a name="parameters"></a>参数  
 `strObj`  
 必需。 `String` 对象或字符串。  
  
 `substring`  
 必需。 要搜索的子字符串。  
  
 `startindex`  
 可选。 在搜索的起始索引。 如果省略，则在字符串末尾开始执行搜索。  
  
## <a name="remarks"></a>备注  
 **LastIndexOf**方法返回一个整数值，指示内的子字符串的开头`String`对象。 如果未找到子字符串，则返回-1。  
  
 如果 `startindex` 为负，则 `startindex` 将被视为零。 如果它大于最大的字符位置索引，则将它视为可能的最大索引。  
  
 从字符串中的最后一个字符开始执行搜索。 否则，此方法等同于**indexOf**。  
  
 下面的示例演示如何使用**lastIndexOf**方法。  
  
```JavaScript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [indexOf 方法（字符串）](../../javascript/reference/indexof-method-string-javascript.md)