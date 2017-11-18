---
title: "WeakMap 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: WeakMap
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de97f8acb94921090696e9019a1df5d945db7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="weakmap-object-javascript"></a>WeakMap 对象 (JavaScript)
键/值对的集合，其中每个键是一个对象引用。  
  
## <a name="syntax"></a>语法  
  
```  
weakmapObj = new WeakMap()  
```  
  
## <a name="remarks"></a>备注  
 A`WeakMap`不枚举对象。  
  
 如果使用现有键向集合添加值，则新值会替换旧值。  
  
 在`WeakMap`对象，对密钥对象的引用弱。 这意味着，`WeakMap`将不会阻止从密钥对象上发生垃圾回收。 没有引用时 (而不`WeakMap`) 键的对象，垃圾回收器可能会收集键的对象。  
  
## <a name="properties"></a>属性  
 下表列出了 `WeakMap` 对象的属性。  
  
|属性|描述|  
|--------------|-----------------|  
|[构造函数](../../javascript/reference/constructor-property-weakmap.md)|指定创建 `WeakMap` 的函数。|  
|[原型](../../javascript/reference/prototype-property-weakmap.md)|返回对 `WeakMap` 的原型的引用。|  
  
## <a name="methods"></a>方法  
 下表列出了 `WeakMap` 对象的方法。  
  
|方法|描述|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|从 `WeakMap` 中移除所有元素。|  
|[删除](../../javascript/reference/delete-method-weakmap-javascript.md)|移除指定的元素从`WeakMap`。|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|返回从指定的元素`WeakMap`。|  
|[具有](../../javascript/reference/has-method-weakmap-javascript.md)|返回`true`如果`WeakMap`包含指定的元素。|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|将新元素添加到 `WeakMap`。|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|返回的字符串表示形式`WeakMap`。|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|返回指定对象的基元值。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何将成员添加到`WeakMap`对象，然后检索成员。  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]