---
title: "new 运算符 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: new_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: new operator in JavaScript
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ad004abb534d69bed1a1bd9bbd2ae96755544b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="new-operator-javascript"></a>new 运算符 (JavaScript)
创建新对象。  
  
## <a name="syntax"></a>语法  
  
```  
new constructor ([arguments])   
```  
  
## <a name="parameters"></a>参数  
 `constructor`  
 必需。 对象的构造函数。 构造函数不采用任何参数，则可以省略圆括号。  
  
 `arguments`  
 可选。 要传递到新的对象的构造函数的任何参数。  
  
## <a name="remarks"></a>备注  
 `new`运算符将执行以下任务：  
  
-   它与任何成员创建的对象。  
  
-   它为将指针传递给新创建对象作为该对象调用构造函数`this`指针。  
  
-   然后，构造函数初始化根据传递给构造函数的参数的对象。  
  
 这些是有效的用法的示例**新**运算符。  
  
```JavaScript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [function 语句](../../javascript/reference/function-statement-javascript.md)