---
title: "prototype 属性 (Map) |Microsoft 文档"
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
ms.assetid: c7b429cb-97b7-400e-a214-1b18bddd6b02
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45601bdff2dfc8047f2499ab07dcdedd66662fc5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-map"></a>prototype 属性 (Map)
返回对地图的原型的引用。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
map.prototype  
```  
  
## <a name="remarks"></a>备注  
 `map`自变量是映射的名称。  
  
 使用 `prototype` 属性，从而向对象的类提供基本功能集。 对象的新实例“继承”了分配给该对象的原型的行为。  
  
 例如，要将方法添加到返回集的最大元素值的 `Map` 对象，则声明该函数，将其添加至 `Map.prototype`，然后再使用它。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]