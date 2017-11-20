---
title: "propertyIsEnumerable 方法 (Object) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: propertyIsEnumerable
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: propertyIsEnumerable property
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5664732db6a311586f11eb13eee4407fdf81410f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="propertyisenumerable-method-object-javascript"></a>propertyIsEnumerable 方法 (Object) (JavaScript)
确定指定的属性是否可枚举。  
  
## <a name="syntax"></a>语法  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## <a name="parameters"></a>参数  
 `object`  
 必需。 对象的实例。  
  
 `proName`  
 必需。 属性名称的字符串值。  
  
## <a name="remarks"></a>备注  
 `propertyIsEnumerable`方法返回`true`如果`proName`中存在`object`，并且可以使用枚举`For`循环。 `propertyIsEnumerable`方法返回`false`如果`object`不具有指定名称的属性或如果指定的属性不是可枚举。 通常情况下，预定义的属性不是可枚举的但用户定义的属性都是可枚举。  
  
 `propertyIsEnumerable`方法不考虑原型链中的对象。  
  
## <a name="example"></a>示例  
  
```JavaScript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [prototype 属性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)