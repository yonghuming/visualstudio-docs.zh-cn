---
title: "Promise.race 函数 （承诺） |Microsoft 文档"
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fedd512f4565009c8429b43b0d9d93de943d13fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="promiserace-function-promise"></a>Promise.race 函数（承诺）
创建一个新承诺，使其在传入自变量中以第一个承诺解决或拒绝时所用的相同结果值进行解决或拒绝。  
  
## <a name="syntax"></a>语法  
  
```  
Promise.race(iterable)  
```  
  
#### <a name="parameters"></a>参数  
 `iterable`  
 必需。 一个或多个承诺。  
  
## <a name="remarks"></a>备注  
 如果 `iterable` 中的一个承诺处于已解决或已拒绝状态，则 `Promise.race` 返回一个按相同方式解决或拒绝的承诺，即结果值等于用于解决（或拒绝）此承诺的值的方式。 如果 `iterable` 中的多个承诺已解决或已拒绝，则 `Promise.race` 返回一个按迭代第一个承诺的相同方式解决的承诺。 如果 iterable 中的承诺均不解决或拒绝，则从 `Promise.race` 返回的承诺也不进行解决或拒绝。  
  
## <a name="example"></a>示例  
  
```JavaScript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p2 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Promise 对象](../../javascript/reference/promise-object-javascript.md)