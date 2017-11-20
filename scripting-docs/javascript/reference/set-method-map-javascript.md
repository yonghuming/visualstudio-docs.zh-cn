---
title: "set 方法 (Map) (JavaScript) |Microsoft 文档"
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a84a5b2714fde55fba03d581faa851d7245e001
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-map-javascript"></a>set 方法 (Map) (JavaScript)
向映射添加新元素。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
mapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>参数  
 `mapObj`  
 必需。 一个 `Map` 对象。  
  
 `key`  
 必需。 新元素的键。  
  
 `value`  
 必需。 要添加的元素的值。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 返回包含新键/值对的 `Map` 对象。  
  
## <a name="remarks"></a>备注  
 如果使用现有键向集合添加值，则新值会替换旧值。  
  
## <a name="example"></a>示例  
 以下示例演示如何将成员添加到 `Map`，然后检索成员。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]