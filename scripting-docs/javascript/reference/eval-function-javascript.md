---
title: "eval 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: eval
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- eval function
- parsing, code
- parser
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 388e486f58bb70fd192701060a5faefaed8bd98e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="eval-function-javascript"></a>eval 函数 (JavaScript)
计算结果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]代码并执行它。  
  
## <a name="syntax"></a>语法  
  
```  
eval(codeString)   
```  
  
## <a name="parameters"></a>参数  
 `codeString`  
 必需。 A`String`包含有效的值[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]代码。  
  
## <a name="remarks"></a>备注  
 `eval`函数允许动态执行[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]源代码。  
  
 `codeString`字符串进行分析通过[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]分析器和执行。  
  
 代码传递给`eval`函数与调用相同的上下文中执行`eval`函数。  
  
 只要可能，使用[JSON.parse 函数](../../javascript/reference/json-parse-function-javascript.md)进行反序列化 JavaScript 对象表示法 (JSON) 文本。 `JSON.parse`函数会更加安全，以及执行得更快比`eval`函数。  
  
## <a name="example"></a>示例  
 下面的代码将变量初始化`myDate`为一个测试日期。  
  
```JavaScript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**:[全局对象](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [String 对象](../../javascript/reference/string-object-javascript.md)