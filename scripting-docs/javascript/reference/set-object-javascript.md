---
title: "设置对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Set
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5134ec09c9a8642499212af9dd5fd44de0068adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="set-object-javascript"></a>Set 对象 (JavaScript)
可以是任何类型的唯一值的集合。  
  
## <a name="syntax"></a>语法  
  
```  
setObj = new Set()     
```  
  
## <a name="remarks"></a>备注  
 如果你尝试添加到一个非唯一值`Set`，新值不会添加到集合。  
  
## <a name="properties"></a>属性  
 下表列出了 `Set` 对象的属性。  
  
|属性|描述|  
|--------------|-----------------|  
|[构造函数](../../javascript/reference/constructor-property-set.md)|指定创建集的函数。|  
|[原型](../../javascript/reference/prototype-property-set.md)|为集返回对原型的引用。|  
|[size](../../javascript/reference/size-property-set-javascript.md)|返回一组中的元素的数目。|  
  
## <a name="methods"></a>方法  
 下表列出了 `Set` 对象的方法。  
  
|方法|描述|  
|------------|-----------------|  
|[add](../../javascript/reference/add-method-set-javascript.md)|向集添加新元素。|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|从集中移除所有元素。|  
|[删除](../../javascript/reference/delete-method-set-javascript.md)|从集中移除指定元素。|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|一组中每个元素执行指定的操作。|  
|[具有](../../javascript/reference/has-method-set-javascript.md)|如果集包含指定的元素，则返回 `true`。|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|返回的字符串表示形式一组。|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|返回指定对象的基元值。|  
  
## <a name="example"></a>示例  
 以下示例演示如何将成员添加到集，然后检索成员。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]