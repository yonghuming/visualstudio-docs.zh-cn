---
title: "Symbol.for 函数 (JavaScript) |Microsoft 文档"
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b7e47c00fbaa321d71a3eeba79e523eee719fb2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="symbolfor-function-javascript"></a>Symbol.for 函数 (JavaScript)
返回指定密钥的符号，或者，如果密钥不存在，则使用新密钥创建新符号对象。  
  
## <a name="syntax"></a>语法  
  
```vb  
Symbol.for(key);  
```  
  
#### <a name="parameters"></a>参数  
 `key`  
 必需。 符号的密钥，还用作说明。  
  
## <a name="remarks"></a>备注  
 此方法搜索全局符号注册表中的符号。 如果将符号序列化为字符串形式，则使用全局符号注册表，以确保针对所有查找项，特定字符串映射到正确符号。  
  
## <a name="example"></a>示例  
  
```JavaScript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]