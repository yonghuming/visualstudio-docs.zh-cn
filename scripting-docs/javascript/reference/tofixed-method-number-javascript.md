---
title: "toFixed 方法 (Number) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toFixed
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toFixed method
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51dd67632f4e6417fee72fd19575025423bbf1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tofixed-method-number-javascript"></a>toFixed 方法 (Number) (JavaScript)
表示定点表示法表示的数字。  
  
## <a name="syntax"></a>语法  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## <a name="parameters"></a>参数  
 `numObj`  
 需要一个`Number`对象。  
  
 `fractionDigits`  
 可选。 小数点后的数字个数。 必须在范围 0-20，（含)。  
  
## <a name="return-value"></a>返回值  
 在定点表示法中，返回的字符串表示形式大量包含`fractionDigits`小数点后的位数。  
  
 如果`fractionDigits`未提供或**未定义**，默认值为 0。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用`toFixed`。  
  
```JavaScript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**: [Number 对象](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [toExponential 方法 (Number)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision 方法 (Number)](../../javascript/reference/toprecision-method-number-javascript.md)