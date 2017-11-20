---
title: "get 方法 (Map) (JavaScript) |Microsoft 文档"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 243d5aa93289cb7a13b34567b7824d028151bad3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-map-javascript"></a>get 方法 (Map) (JavaScript)
从地图返回指定的元素。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
mapObj.get(key)  
```  
  
#### <a name="parameters"></a>参数  
 `mapObj`  
 必需。 一个 `Map` 对象。  
  
 `key`  
 必需。 中的某个元素的键`Map`。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 返回与键关联的对象。 如果`Map`不包含密钥，此方法返回`undefined`值。  
  
## <a name="example"></a>示例  
 下面的示例演示如何检索元素`Map`对象。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]