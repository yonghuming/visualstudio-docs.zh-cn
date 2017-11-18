---
title: "String.fromCharCode 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: fromCharCode
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- fromCharCodeAt method
- characters, from Unicode
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbcd9062d7da0b73647c1d9eb6cc207af23c3532
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="stringfromcharcode-function-javascript"></a>String.fromCharCode 函数 (JavaScript)
从若干 Unicode 字符值中返回一个字符串。  
  
## <a name="syntax"></a>语法  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## <a name="parameters"></a>参数  
 `String`  
 必需。 `String` 对象。  
  
 `code1`, . . . , `codeN`  
 可选。 要转换为字符串的 Unicode 字符值的一系列。 如果未不提供任何参数，则结果为空字符串。  
  
## <a name="remarks"></a>备注  
 在调用此函数`String`对象而不是在字符串实例。  
  
 下面的示例演示如何使用此方法：  
  
```JavaScript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [charCodeAt 方法 (String)](../../javascript/reference/charcodeat-method-string-javascript.md)