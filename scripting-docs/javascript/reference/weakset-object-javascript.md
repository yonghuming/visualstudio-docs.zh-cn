---
title: "WeakSet 对象 (JavaScript) |Microsoft 文档"
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e42849c03f698d6ed5f8b0e28725c85555a74d2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="weakset-object-javascript"></a>WeakSet 对象 (JavaScript)
可以是任何类型的唯一对象的集合。  
  
## <a name="syntax"></a>语法  
  
```  
setObj = new WeakSet()  
```  
  
## <a name="remarks"></a>备注  
 如果尝试将非唯一对象添加到 `WeakSet` 中，则新对象不会被添加到集合中。  
  
 与 `Set` 不同，仅可能将对象添加到集合中。 无法将任意值添加到集合中。  
  
 在`WeakSet`对象，对集中对象的引用弱。 这表示 `WeakSet` 将不会阻止对象上发生垃圾回收。 没有对（除 `WeakSet` 以外）对象的引用时，垃圾回收器可能会收集这些对象。  
  
 `WeakSet`（或 `WeakMap`）可能在某些涉及对象缓存或对象元数据的方案中很有用。 例如，不可扩展对象的元数据可能存储在 `WeakSet` 中，也可以使用 `WeakSet` 来创建用户映像的缓存。  
  
## <a name="properties"></a>属性  
 下表列出了 `WeakSet` 对象的属性。  
  
|属性|说明|  
|--------------|-----------------|  
|构造函数|指定创建集的函数。|  
|原型|为集返回对原型的引用。|  
  
## <a name="methods"></a>方法  
 下表列出了 `WeakSet` 对象的方法。  
  
|方法|说明|  
|------------|-----------------|  
|添加|向集添加新元素。|  
|删除|从集中移除指定元素。|  
|具有|如果集包含指定的元素，则返回 `true`。|  
  
## <a name="example"></a>示例  
 以下示例演示如何向集添加成员，然后验证已添加成员。  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]