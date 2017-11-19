---
title: "delete 运算符 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: delete_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- array elements, deleting
- properties, deleting
- delete operator
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee3def1977c0b29ee14ebf836f2d9ebb51d5a5ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="delete-operator-javascript"></a>delete 运算符 (JavaScript)
删除对象中的属性，或移除数组中的元素。  
  
## <a name="syntax"></a>语法  
  
```  
delete expression  
```  
  
## <a name="remarks"></a>备注  
 `expression`自变量是一个有效[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]表达式，通常会导致属性名称或数组元素。  
  
 如果结果`expression`是一个对象中, 指定的属性`expression`存在，并且该对象不允许它要删除、`false`返回。  
  
 在所有其他情况下，`true`返回。  
  
## <a name="example"></a>示例  
 下面的示例演示如何从数组中移除元素。  
  
```JavaScript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何删除从对象的属性。  
  
```JavaScript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)