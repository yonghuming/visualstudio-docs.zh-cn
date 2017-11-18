---
title: "Object.assign 函数 （对象） (JavaScript) |Microsoft 文档"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c156369299e58eac556d43a87476de2ce09173e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectassign-function-object-javascript"></a>Object.assign 函数（对象）(JavaScript)
将来自一个或多个源对象中的值复制到一个目标对象。  
  
## <a name="syntax"></a>语法  
  
```  
Object.assign(target, ...sources );  
```  
  
#### <a name="parameters"></a>参数  
 `target`  
 必需。 可枚举属性复制到的对象。  
  
 `...sources`  
 必需。 从其中复制可枚举属性的对象。  
  
## <a name="exceptions"></a>异常  
 如果存在分配错误，此函数将引发 `TypeError`，这将终止复制操作。 如果目标属性不可写，则将引发 `TypeError`。  
  
## <a name="remarks"></a>备注  
 此函数返回目标对象。 仅*可枚举自己*属性从源对象复制到目标对象。 可使用此函数合并或克隆对象。  
  
 `null` 或 `undefined` 源被视为空对象一样对待，不会对目标对象产生任何影响。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何使用 `Object.assign` 合并对象。  
  
```JavaScript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何使用 `Object.assign` 克隆对象。  
  
```JavaScript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]