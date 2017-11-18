---
title: "get 方法 (WeakMap) (JavaScript) |Microsoft 文档"
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29decb7e6a050188b75639eb7cf4f27494b31da2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-weakmap-javascript"></a>get 方法 (WeakMap) (JavaScript)
返回从指定的元素`WeakMap`对象。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
weakmapObj.get(key)  
```  
  
#### <a name="parameters"></a>参数  
 `weakmapObj`  
 必需。 一个 `WeakMap` 对象。  
  
 `key`  
 必需。 中的某个元素的键`WeakMap`。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 返回与键关联的对象。 如果`WeakMap`不包含密钥，此方法返回`undefined`值。  
  
## <a name="example"></a>示例  
 下面的示例演示如何检索成员从`WeakMap`对象。  
  
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