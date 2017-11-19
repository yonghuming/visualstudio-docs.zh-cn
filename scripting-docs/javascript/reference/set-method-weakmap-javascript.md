---
title: "set 方法 (WeakMap) (JavaScript) |Microsoft 文档"
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c916bda13c7bd973b37c4e4cb6b81e327ee5de54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-weakmap-javascript"></a>set 方法 (WeakMap) (JavaScript)
向 `WeakMap` 对象添加新元素。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
weakmapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>参数  
 `weakmapObj`  
 必需。 一个 `WeakMap` 对象。  
  
 `key`  
 必需。 一个表示要添加元素的键的对象。 它必须是对象引用。  
  
 `value`  
 必需。 要添加的元素的值。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 返回包含新键/值对的 `WeakMap` 对象。  
  
## <a name="remarks"></a>备注  
 如果使用现有键向集合添加值，则新值会替换旧值。  
  
## <a name="example"></a>示例  
 以下示例演示如何向 `WeakMap` 对象添加成员。  
  
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
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]