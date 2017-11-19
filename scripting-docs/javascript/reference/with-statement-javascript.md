---
title: "with 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: with_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: With statement
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35d49b13261c66cde0ecd53517a99361f6aecb79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="with-statement-javascript"></a>with 语句 (JavaScript)
创建语句的默认对象。  
  
## <a name="syntax"></a>语法  
  
```  
with (object) {  
    statements  
}   
```  
  
## <a name="parameters"></a>参数  
 `object`  
 默认对象。  
  
 `statements`  
 `object` 作为默认对象的一个或多个语句。  
  
## <a name="remarks"></a>备注  
 `with` 语句通常用来减少特定情形下必须写入的代码数量。  
  
> [!WARNING]
>  在严格模式中不允许使用 `with`。 使用 `with` 会导致代码更难读取和调试，因此通常应当避免。  
  
## <a name="example"></a>示例  
 在此示例中，`Math` 对象重复使用：  
  
```JavaScript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## <a name="example"></a>示例  
 如果重写该示例以使用 `with` 语句，你的代码将变得更加简洁：  
  
```JavaScript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [this 语句](../../javascript/reference/this-statement-javascript.md)