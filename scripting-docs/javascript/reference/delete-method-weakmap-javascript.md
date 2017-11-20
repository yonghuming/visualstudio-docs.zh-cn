---
title: "delete 方法 (WeakMap) (JavaScript) |Microsoft 文档"
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4cec06b77b7198e23d7e455849b5c0bf6d7ff9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-weakmap-javascript"></a>delete 方法 (WeakMap) (JavaScript)
从 `WeakMap` 对象移除指定元素。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
weakmapObj.delete(key)  
```  
  
#### <a name="parameters"></a>参数  
 `weakmapObj`  
 必需。 一个 `WeakMap` 对象。  
  
 `key`  
 必需。 要移除的元素的键。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 如果已移除元素，则为 `true`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将成员添加到`WeakMap`然后将其删除。  
  
```JavaScript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]