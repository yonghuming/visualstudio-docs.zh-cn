---
title: "Map 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Map
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d89890f9fecaf61e47e136734ed7fefb7b73cabd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="map-object-javascript"></a>Map 对象 (JavaScript)
键/值对的集合。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
mapObj = new Map()  
```  
  
## <a name="remarks"></a>备注  
 键和集合中的值可以是任何类型。 如果使用现有键向集合添加值，则新值会替换旧值。  
  
## <a name="properties"></a>属性  
 下表列出了 `Map` 对象的属性。  
  
|属性|描述|  
|--------------|-----------------|  
|[构造函数](../../javascript/reference/constructor-property-map.md)|指定创建一个映射的函数。|  
|[原型](../../javascript/reference/prototype-property-map.md)|返回对地图的原型的引用。|  
|[size](../../javascript/reference/size-property-map-javascript.md)|返回映射中的元素数。|  
  
## <a name="methods"></a>方法  
 下表列出了 `Map` 对象的方法。  
  
|方法|描述|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|从映射中移除所有元素。|  
|[删除](../../javascript/reference/delete-method-map-javascript.md)|从映射中删除指定的元素。|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|地图中每个元素执行指定的操作。|  
|[get](../../javascript/reference/get-method-map-javascript.md)|从地图返回指定的元素。|  
|[具有](../../javascript/reference/has-method-map-javascript.md)|返回`true`如果映射包含指定的元素。|  
|[set](../../javascript/reference/set-method-map-javascript.md)|向映射添加新元素。|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|返回的字符串表示形式映射。|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|返回指定对象的基元值。|  
  
## <a name="example"></a>示例  
 以下示例演示如何将成员添加到 `Map`，然后检索成员。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]