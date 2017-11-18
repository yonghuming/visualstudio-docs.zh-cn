---
title: "Promise.resolve 函数 （承诺） |Microsoft 文档"
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d815c9c23da48c877f7f1d995df8991429375e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="promiseresolve-function-promise"></a>Promise.resolve 函数（承诺）
创建新的已解决承诺，该承诺的结果等于其自变量。  
  
## <a name="syntax"></a>语法  
  
```  
Promise.resolve(x)  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 必需。 与已完成承诺一起返回的值。  
  
## <a name="remarks"></a>备注  
 当返回已完成承诺对象时，将运行 `then` 方法的履行处理函数。  
  
## <a name="example"></a>示例  
  
```JavaScript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Promise 对象](../../javascript/reference/promise-object-javascript.md)