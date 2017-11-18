---
title: "has 方法 (Map) (JavaScript) |Microsoft 文档"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48228b495c845bef91caa0b85e67980100a6f790
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-map-javascript"></a>has 方法 (Map) (JavaScript)
返回`true`如果映射包含指定的元素。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
mapObj.has(key)  
```  
  
#### <a name="parameters"></a>参数  
 `mapObj`  
 必需。 一个 `Map` 对象。  
  
 `key`  
 必需。 要测试的元素的键。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 `true`如果映射包含指定的元素。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将成员添加到`Map`，然后检查 map 中是否包含它。  
  
```JavaScript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]