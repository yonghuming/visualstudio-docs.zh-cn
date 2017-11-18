---
title: "compile 方法 （正则表达式） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: compile
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- regular expressions, compiling
- Compile method
- compiling source code, regular expressions
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b8de23a9e4f0e03fbf042195867ad9426e4c6bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="compile-method-regular-expression-javascript"></a>compile 方法（正则表达式）(JavaScript)
将编译为内部格式的执行速度更快的正则表达式。  
  
## <a name="syntax"></a>语法  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## <a name="parameters"></a>参数  
 `rgExp`  
 必需。 实例**正则表达式**对象。 可以是变量的名称或文本。  
  
 *模式*  
 必需。 包含要编译的正则表达式模式的字符串表达式  
  
 `flags`  
 可选。 可以组合的可用标志包括：  
  
-   g (全局搜索出现的所有*模式*)  
  
-   i（忽略大小写）  
  
-   m（多行搜索）  
  
## <a name="remarks"></a>备注  
 **编译**方法将*模式*为内部格式的执行速度更快。 这样更有效地使用正则表达式在循环中，例如。 已编译的正则表达式可加快操作在反复重用同一个表达式。 获得什么特别的用处，但是，如果正则表达式更改时。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**编译**方法：  
  
```JavaScript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**:[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)