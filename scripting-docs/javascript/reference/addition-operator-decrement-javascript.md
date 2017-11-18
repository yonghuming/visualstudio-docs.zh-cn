---
title: "加法运算符 （+） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arithmetic operators, addition
- strings [Visual Studio], concatenating
- concatenation operators, vs. addition operator
- addition operator
- + operator
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70ff02b1f234da7b88d28e66da82262ccef7bfaf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="addition-operator--javascript"></a>加法运算符 (+) (JavaScript)
一个数值表达式的值添加到另一个，或串联两个字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = expression1 + expression2  
```  
  
## <a name="parameters"></a>参数  
 `result`  
 任何变量。  
  
 `expression1`  
 任何表达式。  
  
 `expression2`  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 两个表达式的类型确定的行为 **+** 运算符。  
  
|如果|Then|  
|--------|----------|  
|两个表达式均数值或布尔|添加|  
|这两个表达式均为字符串|连接|  
|一个表达式是数值和另一种是一个字符串|连接|  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [加法赋值运算符 （+ =）](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)