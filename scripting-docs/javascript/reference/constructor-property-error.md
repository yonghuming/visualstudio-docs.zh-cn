---
title: "constructor 属性 （错误） |Microsoft 文档"
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
ms.assetid: 18aea278-2bd5-457b-83a5-d8d8f1226e0c
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1ade0ab1ba771b2ff9dfb7051b2983b3da77ed4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-error"></a>constructor 属性（错误）
指定创建一条错误的函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
error.constructor  
```  
  
## <a name="remarks"></a>备注  
 所需`error`是错误对象的名称。  
  
 `constructor` 属性是具有原型的每个对象的原型的成员。 `constructor` 属性包含对构造特定对象实例的函数的引用。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用构造函数属性。  
  
```JavaScript  
var x = new Error("This is an error");  
  
if (x.constructor == Error)  
    document.write("Object is an error.");  
  
// Output:  
// Object is an error.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]