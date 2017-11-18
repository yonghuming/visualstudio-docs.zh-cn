---
title: "in 运算符 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: in_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: in operator
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eefcd4c53d2e3366a26f0d8dfb099f59038507ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="in-operator-javascript"></a>in 运算符 (JavaScript)
测试某个对象中是否存在某个属性。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = property in object  
```  
  
## <a name="parameters"></a>参数  
 `result`  
 必需。 任何变量。  
  
 `property`  
 必需。 一个表达式，计算结果为字符串表达式。  
  
 `object`  
 必需。 任何对象。  
  
## <a name="remarks"></a>备注  
 `in`运算符确定一个对象是否具有名为的属性`property`。 它还确定属性是否为对象的原型链的一部分。 有关对象原型的详细信息，请参阅[原型和原型继承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`in`运算符：  
  
```JavaScript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)