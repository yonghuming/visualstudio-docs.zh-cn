---
title: "has 方法 (WeakMap) (JavaScript) |Microsoft 文档"
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9a1706a1b96b5273ec280c4cef2be47a3bc6e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-weakmap-javascript"></a>has 方法 (WeakMap) (JavaScript)
返回`true`如果`WeakMap`对象包含指定的元素。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
weakmapObj.has(key)  
```  
  
#### <a name="parameters"></a>参数  
 `weakmapObj`  
 必需。 一个 `WeakMap` 对象。  
  
 `key`  
 必需。 要测试的元素的键。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 `true`如果`WeakMap`包含指定的键。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将成员添加到`WeakMap`，然后使用`has`以检查是否存在。  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]