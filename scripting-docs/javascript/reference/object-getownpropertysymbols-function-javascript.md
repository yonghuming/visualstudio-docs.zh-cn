---
title: "Object.getOwnPropertySymbols 函数 (JavaScript) |Microsoft 文档"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bcddba77305e30e4c5ae13f6b1fc5c9385b7108
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Object.getOwnPropertySymbols 函数 (JavaScript)
返回对象的自有符号属性。 对象的自有符号属性是指直接在此对象上定义、而非从对象的原型继承的属性。  
  
## <a name="syntax"></a>语法  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>参数  
 `object`  
 必需。 包含自有符号的对象。  
  
## <a name="return-value"></a>返回值  
 包含对象的自有符号的数组。  
  
## <a name="remarks"></a>备注  
 需要使用 `Object.getOwnPropertySymbols` 来获取对象的符号属性。 `Object.getOwnPropertyNames` 不会返回符号属性。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何获取对象的符号属性。  
  
```JavaScript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]