---
title: "delete 方法 (Map) (JavaScript) |Microsoft 文档"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5185b883cf603acdc91fe1f1c833d337c4468ba4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-map-javascript"></a>delete 方法 (Map) (JavaScript)
从映射中移除指定的元素。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
mapObj.delete(key)  
```  
  
#### <a name="parameters"></a>参数  
 `mapObj`  
 必需。 一个 `Map` 对象。  
  
 `key`  
 必需。 要移除的元素的键。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 如果已移除元素，则为 `true`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将成员添加到`Map`，然后删除至少其中一个。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]