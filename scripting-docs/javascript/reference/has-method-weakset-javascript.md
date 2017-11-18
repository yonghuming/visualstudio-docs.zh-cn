---
title: "has 方法 (WeakSet) (JavaScript) |Microsoft 文档"
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dbc7e17e3fd73730386293c5e3f894455e41a93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-weakset-javascript"></a>has 方法 (WeakSet) (JavaScript)
如果 `WeakSet` 包含指定的元素，则返回 `true`。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
setObj.has(obj)  
```  
  
#### <a name="parameters"></a>参数  
 `setObj`  
 必需。 一个 `WeakSet` 对象。  
  
 `obj`  
 必需。 要测试的元素。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 如果该集包含指定的元素，则为 `true`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将成员添加到 `WeakSet`，然后检查集是否包含特定成员。  
  
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