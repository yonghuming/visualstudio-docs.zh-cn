---
title: "Object 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: object
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Object object
ms.assetid: d24ef8fc-217b-4828-94e1-19f72780bae0
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17e82b9c66c286c7f847e7b67b1b5928aadd613e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="object-object-javascript"></a>Object 对象 (JavaScript)
提供对所有 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象通用的功能。  
  
## <a name="syntax"></a>语法  
  
```  
  
obj  
 = new Object([value])   
```  
  
## <a name="parameters"></a>参数  
 `obj`  
 必需。 `Object` 对象分配到的变量名称。  
  
 *值*  
 可选。 任一 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 基元数据类型（数字、布尔值或字符串）。 如果值是一个对象，则返回的对象是未修改的。 如果*值*是`null`，**未定义**，或未提供，创建具有任何内容的对象。  
  
## <a name="remarks"></a>备注  
 `Object` 对象包含在所有其他 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象中；它的所有方法和属性均可用于所有其他对象。 方法可在用户定义的对象中进行重新定义，并由 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 在适当时间调用。 **ToString**方法是频繁重新定义的一个示例`Object`方法。  
  
 在此语言参考中，每个 `Object` 方法的说明均包括内部 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象的默认和对象特定的实现信息。  
  
## <a name="requirements"></a>要求  
 `Object Object`中已引入 [!INCLUDE[jsv3text](../../javascript/reference/includes/jsv3text-md.md)]。 更高版本中已引入以下列表中的某些成员。  
  
## <a name="properties"></a>属性  
 下表列出了 `Object Object` 的属性。  
  
|属性|描述|  
|--------------|-----------------|  
|[__proto\_ \_属性](../../javascript/reference/proto-property-object-javascript.md)|指定对象的原型。|  
|[constructor 属性](../../javascript/reference/constructor-property-object-javascript.md)|指定用于创建对象的函数。|  
|[prototype 属性](../../javascript/reference/prototype-property-object-javascript.md)|为对象的类返回原型的引用。|  
  
## <a name="functions"></a>函数  
 下表列出了 `Object Object` 的函数。  
  
|函数|描述|  
|--------------|-----------------|  
|[Object.assign 函数](../../javascript/reference/object-assign-function-object-javascript.md)|将来自一个或多个源对象中的值复制到一个目标对象。|  
|[Object.create 函数](../../javascript/reference/object-create-function-javascript.md)|创建具有指定原型并可选择包含指定属性的对象。|  
|[Object.defineProperties 函数](../../javascript/reference/object-defineproperties-function-javascript.md)|将一个或多个属性添加到对象，和/或修改现有属性的特性。|  
|[Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)|将属性添加到对象，或修改现有属性的特性。|  
|[Object.freeze 函数](../../javascript/reference/object-freeze-function-javascript.md)|防止修改现有属性的特性和值，并防止添加新属性。|  
|[Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|返回数据属性或访问器属性的定义。|  
|[Object.getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md)|返回对象属性及方法的名称。|  
|[Object.getOwnPropertySymbols 函数](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)|返回对象的符号属性。|  
|[Object.getPrototypeOf 函数](../../javascript/reference/object-getprototypeof-function-javascript.md)|返回某个对象的原型。|  
|[Object.is 函数](../../javascript/reference/object-is-function-javascript.md)|返回一个值，该值指示两个值是否相同。|  
|[Object.isExtensible 函数](../../javascript/reference/object-isextensible-function-javascript.md)|返回指示是否可将新属性添加到对象的值。|  
|[Object.isFrozen 函数](../../javascript/reference/object-isfrozen-function-javascript.md)|如果无法在对象中修改现有属性的特性和值，并且无法将新属性添加到对象，则返回 `true`。|  
|[Object.isSealed 函数](../../javascript/reference/object-issealed-function-javascript.md)|如果无法在对象中修改现有属性特性，并且无法将新属性添加到对象，则返回 `true`。|  
|[Object.keys 函数](../../javascript/reference/object-keys-function-javascript.md)|返回对象的可枚举属性和方法的名称。|  
|[Object.preventExtensions 函数](../../javascript/reference/object-preventextensions-function-javascript.md)|防止向对象添加新属性。|  
|[Object.seal 函数](../../javascript/reference/object-seal-function-javascript.md)|防止修改现有属性的特性，并防止添加新属性。|  
|[Object.setPrototypeOf 函数](../../javascript/reference/object-setprototypeof-function-javascript.md)|设置对象的原型。|  
  
## <a name="methods"></a>方法  
 下表列出了 `Object Object` 的方法。  
  
|方法|描述|  
|------------|-----------------|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|返回一个布尔值，该值指示某个对象是否具有指定名称的属性。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|返回一个布尔值，该值指示某个对象是否存在于另一个对象的原型层次结构中。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|返回一个布尔值，该值指示指定属性是否为对象的一部分且是否可枚举。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-method-object-javascript.md)|返回基于当前区域设置转换为字符串的对象。|  
|[toString 方法](../../javascript/reference/tostring-method-object-javascript.md)|返回对象的字符串表示形式。|  
|[valueOf 方法](../../javascript/reference/valueof-method-object-javascript.md)|返回指定对象的基元值。|  
  
## <a name="see-also"></a>另请参阅  
 [JavaScript 对象](../../javascript/reference/javascript-objects.md)