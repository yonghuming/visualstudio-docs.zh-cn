---
title: "then 方法 （承诺） |Microsoft 文档"
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
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeb97fae19ca9923280b5099e3e4d8c839fa2815
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="then-method-promise"></a>then 方法（承诺）
允许你指定实现承诺时要完成的工作。  
  
## <a name="syntax"></a>语法  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### <a name="parameters"></a>参数  
 `promise`  
 必需。 Promise 对象。  
  
 `onCompleted`  
 必需。 承诺成功完成时要运行的履行处理程序函数。  
  
 `onRejected`  
 可选。 承诺被拒绝时要运行的错误处理程序函数。  
  
## <a name="remarks"></a>备注  
 承诺必须完成（返回一个值）或者必须被拒绝（返回一个原因）。 承诺完成或被拒绝时（无论哪一个先发生），Promise 对象的 `then` 方法都会运行。 如果承诺成功完成，则将运行 `then` 方法的履行处理程序函数。 如果承诺被拒绝，则将运行 `then` 方法（或 `catch` 方法）的错误处理程序函数。  
  
## <a name="example"></a>示例  
 下面的示例演示如何调用返回承诺的函数 (`timeout`)。 达到 5000 ms 的超时时间后，将运行 `then` 方法的履行处理程序。  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Promise 对象](../../javascript/reference/promise-object-javascript.md)