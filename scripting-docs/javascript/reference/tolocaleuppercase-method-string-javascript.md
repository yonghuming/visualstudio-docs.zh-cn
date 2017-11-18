---
title: "toLocaleUpperCase 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleUpperCase method
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07a89560dde0319598da30fc3451524112b99eac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaleuppercase-method-string-javascript"></a>toLocaleUpperCase 方法 (String) (JavaScript)
返回一个字符串，其中所有字母字符都被转换为大写形式，并考虑主机环境的当前区域设置。  
  
## <a name="syntax"></a>语法  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## <a name="remarks"></a>备注  
 所需`stringVar`引用是`String`对象或字符串文本。  
  
 `toLocaleUpperCase`方法将转换的字符在字符串中，考虑主机环境的当前区域设置。 在大多数情况下，结果是相同的结果作为`toUpperCase`方法。 如果一种语言的规则与正则 Unicode 大小写映射发生冲突，则结果与不同。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [toLocaleLowerCase 方法 (String)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase 方法 (String)](../../javascript/reference/touppercase-method-string-javascript.md)