---
title: "isPrototypeOf 方法 (Object) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: isPrototypeOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: isPrototypeOf method
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ce97faecfade089bbf0b7a725a02ee73b54718
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="isprototypeof-method-object-javascript"></a>isPrototypeOf 方法 (Object) (JavaScript)
确定一个对象是否存在于另一个对象的原型链中。  
  
## <a name="syntax"></a>语法  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## <a name="parameters"></a>参数  
 `prototype`  
 必需。 对象原型。  
  
 `object`  
 必需。 另一个对象，将对其原型链进行检查。  
  
## <a name="remarks"></a>备注  
 如果 `isPrototypeOf` 的原型链中具有 `true`，则 `object` 方法返回 `prototype`。 原型链用于在同一个对象类型的不同实例之间共享功能。 当 `isPrototypeOf` 不是对象或当 `false` 没有出现在 `object` 的原型链中时，`prototype` 方法返回 `object`。  
  
## <a name="example"></a>示例  
 下面的示例演示 `isPrototypeOf` 方法的用法。  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [prototype 属性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)