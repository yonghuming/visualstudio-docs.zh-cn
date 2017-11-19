---
title: "constructor 属性 （字符串） |Microsoft 文档"
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f1942073a9950a77c7e0cae759a9653318d8a18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-string"></a>constructor 属性（字符串）
指定创建字符串的函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
string.constructor  
```  
  
## <a name="remarks"></a>备注  
 所需`string`是一个字符串的名称。  
  
 `constructor` 属性是具有原型的每个对象的原型的成员。 这包括所有内部[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象除外`Global`和`Math`对象。 `constructor` 属性包含对构造特定对象实例的函数的引用。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用构造函数属性。  
  
```JavaScript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]