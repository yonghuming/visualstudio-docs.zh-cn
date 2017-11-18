---
title: "为..的语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47154261fd4817ba95b8884bd6482a87e044a5a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="forof-statement-javascript"></a>for...of 语句 (JavaScript)
对从可迭代对象中获取的迭代器的每个值执行一个或多个语句。  
  
## <a name="syntax"></a>语法  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## <a name="parameters"></a>参数  
 `variable`  
 必需。 可为 `object` 的任何属性值的变量。  
  
 `object`  
 必需。 等可迭代对象`Array`， `Map`， `Set`，或实现的对象[迭代器接口](http://msdn.microsoft.com/en-us/3692355a-a703-4d43-8fb5-c03b4b7e8db1)。  
  
 `statements`  
 可选。 要为 `object` 的每个值执行的一个或多个语句。 可以是复合语句。  
  
## <a name="remarks"></a>备注  
 在循环的每个迭代的开头，`variable` 的值是 `object` 的下一个属性值。  
  
## <a name="example"></a>示例  
 下面的示例阐释了如何使用数组上的 `for...of` 语句。  
  
```JavaScript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## <a name="example"></a>示例  
 下面的示例阐释了如何使用 `Map` 对象上的 `for...of` 语句。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [为..语句中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)