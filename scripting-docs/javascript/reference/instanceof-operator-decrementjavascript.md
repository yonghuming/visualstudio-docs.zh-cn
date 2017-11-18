---
title: "instanceof 运算符 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 672047cb066a812d16edc693638c3d6d8295798b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="instanceof-operator-javascript"></a>instanceof 运算符 (JavaScript)
返回一个布尔值，该值指示对象是否为特定类的实例。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>参数  
 `result`  
 必需。 任何变量。  
  
 `object`  
 必需。 任何对象表达式。  
  
 `class`  
 必需。 任何定义的对象类。  
  
## <a name="remarks"></a>备注  
 如果 `instanceof` 是 `true` 的一个实例，则 `object` 运算符返回 `class`。 如果 `true` 存在于对象的原型链中（为 `true`），则该运算符返回 `class`。 如果 `false` 不是 `object` 的实例，或 `class` 为 `object`，则该运算符返回 `null`。  
  
## <a name="example"></a>示例  
 以下示例演示如何使用 `instanceof` 运算符。  
  
```JavaScript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)