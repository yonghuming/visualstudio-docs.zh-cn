---
title: "prototype 属性 （字符串） |Microsoft 文档"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df8c6abbd64fce9172d805c2e22dee51f4fbbee4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-string"></a>prototype 属性（字符串）
返回对字符串的类的原型的引用。  
  
## <a name="syntax"></a>语法  
  
```  
  
string.prototype  
```  
  
## <a name="remarks"></a>备注  
 `string`自变量是字符串的名称。  
  
 使用 `prototype` 属性，从而向对象的类提供基本功能集。 对象的新实例“继承”了分配给该对象的原型的行为。  
  
 例如，若要将方法添加到`String`对象，它返回字符串的最后一个元素的值，请声明该函数，将其添加到`String.prototype`，然后使用它。  
  
```JavaScript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 所有内部[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象具有`prototype`属性是只读的。 属性和方法可能添加至原型，但该对象可能无法为指定其他原型。 但是，可能将用户定义的对象分配的新原型。  
  
 此语言参考中每个内部函数对象的方法和属性列表指示哪些是属于该对象的原型，哪些不是。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]