---
title: "toLocaleLowerCase 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleLowerCase method
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 642ced387e0d3b4cf763767ec147d6160ed7d36b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalelowercase-method-string-javascript"></a>toLocaleLowerCase 方法 (String) (JavaScript)
将转换为小写的所有字母字符考虑主机环境的当前区域设置。  
  
## <a name="syntax"></a>语法  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## <a name="remarks"></a>备注  
 所需`stringVar`引用是`String`对象或字符串文本。  
  
 `toLocaleLowerCase`方法将转换的字符在字符串中，考虑主机环境的当前区域设置。 在大多数情况下，结果都是相同的结果作为`toLowerCase`方法。 如果一种语言的规则与正则 Unicode 大小写映射发生冲突，则结果与不同。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [toLocaleUpperCase 方法 (String)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase 方法](../../javascript/reference/tolowercase-method-javascript.md)