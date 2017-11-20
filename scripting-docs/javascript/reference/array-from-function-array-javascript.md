---
title: "Array.from 函数 （数组） (JavaScript) |Microsoft 文档"
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a240cb439942bfeb6b4c9a1febb4d24cef1c5c18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="arrayfrom-function-array-javascript"></a>Array.from 函数（数组）(JavaScript)
从类似数组的对象或可迭代的对象返回一个数组。  
  
## <a name="syntax"></a>语法  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### <a name="parameters"></a>参数  
 `arrayLike`  
 必需。 类似数组的对象或可迭代的对象。  
  
 `mapfn`  
 可选。 要对 `arrayLike` 中的每个元素调用的映射函数。  
  
 `thisArg`  
 可选。 指定映射函数中的 `this` 对象。  
  
## <a name="remarks"></a>备注  
 `arrayLike` 参数必须是具有编制索引的元素和 `length` 属性的对象或可迭代对象，如 `Set` 对象。  
  
 对数组中每个元素调用了可选映射函数。  
  
## <a name="example"></a>示例  
 下面的示例从 DOM 元素节点集合中返回一个数组。  
  
```JavaScript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## <a name="example"></a>示例  
 下面的示例返回一个字符数组。  
  
```JavaScript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## <a name="example"></a>示例  
 下面的示例返回集合中包含的对象数组。  
  
```JavaScript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";   
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用箭头语法和映射函数更改元素的值。  
  
```JavaScript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]