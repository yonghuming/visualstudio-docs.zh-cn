---
title: "加法赋值运算符 （+ =） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- addition assignment operator (+=)
- += operator
- assignment operators, JavaScript
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38d86c537dda90dd7f44923b97384b3609dad5ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="addition-assignment-operator--javascript"></a>加法赋值运算符 (+=) (JavaScript)
将表达式值添加到变量值，并将结果赋给该变量。  
  
## <a name="syntax"></a>语法  
  
```  
  
result += expression   
```  
  
## <a name="parameters"></a>参数  
 `result`  
 任何变量。  
  
 `expression`  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 使用此运算符是完全相同的与指定： `result = result + expression`。  
  
 两个表达式的类型确定的行为`+=`运算符。  
  
|如果|Then|  
|--------|----------|  
|两个表达式均数值或布尔|添加|  
|这两个表达式均为字符串|连接|  
|一个表达式是数值和另一种是一个字符串|连接|  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [加法运算符 （+）](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)