---
title: "prototype 属性 （错误） |Microsoft 文档"
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7d0413d3541691a38672e7c0720b58245725b76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-error"></a>prototype 属性（错误）
返回对错误的原型的引用。  
  
## <a name="syntax"></a>语法  
  
```  
  
error.prototype  
```  
  
## <a name="remarks"></a>备注  
 `error`参数是错误的名称。  
  
 使用`prototype`属性向错误提供一组基本的功能。 对象的新实例“继承”了分配给该对象的原型的行为。  
  
 例如，要将方法添加到返回数组的最大元素值的 `Error` 对象，请声明该函数，将其添加至 `Error.prototype`，然后再使用它。  
  
```JavaScript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 所有内部[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象具有`prototype`属性是只读的。 属性和方法可能添加至原型，但该对象可能无法为指定其他原型。 但是，可能将用户定义的对象分配的新原型。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]