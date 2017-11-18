---
title: "delete 方法 (WeakSet) (JavaScript) |Microsoft 文档"
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
ms.assetid: 19e93366-7d42-4abf-b7b9-fcf943fa17a3
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46eeac8ddd0072712c1867bc2a419a4e3255ffd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-weakset-javascript"></a>delete 方法 (WeakSet) (JavaScript)
从 `WeakSet` 中移除指定元素。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
weaksetObj.delete(obj)  
```  
  
#### <a name="parameters"></a>参数  
 `weaksetObj`  
 必需。 一个 `WeakSet` 对象。  
  
 `obj`  
 必需。 要移除的元素。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 如果已移除元素，则为 `true`。  
  
## <a name="example"></a>示例  
 下面的示例演示了如何添加和删除 `WeakSet` 的元素。  
  
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