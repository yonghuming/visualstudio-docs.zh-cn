---
title: "toExponential 方法 (Number) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toExponential
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toExponential method
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fff2f2bc0c443fa9308c8d01dcea42a3cec9ff04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="toexponential-method-number-javascript"></a>toExponential 方法 (Number) (JavaScript)
表示指数记数法的数字。  
  
## <a name="syntax"></a>语法  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## <a name="parameters"></a>参数  
 `numObj`  
 必需。 A**数**对象。  
  
 `fractionDigits`  
 可选。 小数点后的数字个数。 必须在范围 0-20，（含)。  
  
## <a name="return-value"></a>返回值  
 返回指数记数法中的数字的字符串表示。 字符串包含小数点前, 一个数字，并且可能包含`fractionDigits`在它后面的数字。  
  
 如果`fractionDigits`未提供，`toExponential`方法返回尽可能多的数字必须唯一指定数。  
  
## <a name="example"></a>示例  
  
```JavaScript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**: [Number 对象](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [toFixed 方法 (Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision 方法 (Number)](../../javascript/reference/toprecision-method-number-javascript.md)