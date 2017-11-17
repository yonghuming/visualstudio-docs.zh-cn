---
title: "add 方法 (WeakSet) (JavaScript) |Microsoft 文档"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ab486beaba4a26c73930b5ceaee927f73aa077a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="add-method-weakset-javascript"></a>add 方法 (WeakSet) (JavaScript)
将新元素添加到 `WeakSet`。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
weaksetObj.add(obj)  
```  
  
#### <a name="parameters"></a>参数  
 `weaksetObj`  
 必需。 一个 `WeakSet` 对象。  
  
 `obj`  
 必需。 `WeakSet` 的新元素。  
  
## <a name="remarks"></a>备注  
 新元素必须是一个对象，而不是任意值，并且必须是唯一的。 如果将非唯一的元素添加到 `WeakSet`，则新元素不会添加到集合中。  
  
## <a name="example"></a>示例  
 以下示例演示如何将成员添加到集并验证它们已被添加。  
  
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