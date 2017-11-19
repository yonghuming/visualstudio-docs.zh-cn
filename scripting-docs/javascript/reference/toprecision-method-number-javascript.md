---
title: "toPrecision 方法 (Number) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toPrecision
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toPrecision method
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeab7642dcd88677d1b5a7102e3cf342d7ee1d29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="toprecision-method-number-javascript"></a>toPrecision 方法 (Number) (JavaScript)
在具有指定位数的数字的指数或定点表示法表示的数字。  
  
## <a name="syntax"></a>语法  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## <a name="parameters"></a>参数  
 `numObj`  
 必需。 一个 `Number` 对象。  
  
 `precision`  
 可选。 小数位数。 必须在范围 1-21 日 （含)。  
  
## <a name="return-value"></a>返回值  
 有关指数记数法中的数字`precision`-1 小数点后返回数字。 对于内固定记数法，编号`precision`返回有效位数。  
  
 如果`precision`未提供或**未定义**、 **toString**改为调用方法。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用`toPrecision`。  
  
```JavaScript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**: [Number 对象](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [toFixed 方法 (Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential 方法 (Number)](../../javascript/reference/toexponential-method-number-javascript.md)