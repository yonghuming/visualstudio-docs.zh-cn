---
title: "delete 方法 (Set) (JavaScript) |Microsoft 文档"
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72762b93c6996fd72bd035c5d653f0e85f4ffd33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-set-javascript"></a>delete 方法 (Set) (JavaScript)
从集中删除指定的元素。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
setObj.delete(value)  
```  
  
#### <a name="parameters"></a>参数  
 `setObj`  
 必需。 一个 `Set` 对象。  
  
 `value`  
 必需。 要移除的元素。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 如果已移除元素，则为 `true`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将成员添加到`Set`，然后删除至少其中一个。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]