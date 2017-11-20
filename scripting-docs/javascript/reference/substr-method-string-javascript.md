---
title: "substr 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: substr
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: substr method
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b002bfefbeb81c534c882fa4a4720c93ccca185
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="substr-method-string-javascript"></a>substr 方法 (String) (JavaScript)
获取指定位置开始，并具有指定的长度的子字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## <a name="parameters"></a>参数  
 `stringvar`  
 必需。 字符串文本或`String`对象从其提取子字符串。  
  
 `start`  
 必需。 所需的子字符串的起始位置。 在字符串中的第一个字符的索引为零。  
  
 `length`  
 可选。 要返回的子字符串中包含的字符数。  
  
## <a name="remarks"></a>备注  
 如果`length`为零或负数，则返回一个空字符串。 如果未指定，子字符串将一直到末尾`stringvar`。  
  
## <a name="example"></a>示例  
 下面的示例演示 `substr` 方法的用法。  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [substring 方法 (String)](../../javascript/reference/substring-method-string-javascript.md)