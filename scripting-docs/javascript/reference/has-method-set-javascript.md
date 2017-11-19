---
title: "has 方法 (Set) (JavaScript) |Microsoft 文档"
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9690e3d091e8ae0f9670fd737a29590524834c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-set-javascript"></a>has 方法 (Set) (JavaScript)
返回`true`如果该集包含指定的元素。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
setObj.has(value)  
```  
  
#### <a name="parameters"></a>参数  
 `setObj`  
 必需。 一个 `Set` 对象。  
  
 `value`  
 必需。 要测试的元素。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 如果该集包含指定的元素，则为 `true`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将成员添加到 `Set`，然后检查集是否包含特定成员。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]