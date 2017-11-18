---
title: "Symbol.keyFor 函数 (JavaScript) |Microsoft 文档"
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
ms.assetid: f0b6f034-6d0a-421c-b1c6-52489411e9a3
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22f671a1ea14ce56c52fccbce75893516a10bcc5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="symbolkeyfor-function-javascript"></a>Symbol.keyFor 函数 (JavaScript)
返回指定符号的密钥。  
  
## <a name="syntax"></a>语法  
  
```vb  
Symbol.keyFor(sym);  
```  
  
#### <a name="parameters"></a>参数  
 `sym`  
 必需。 符号对象。  
  
## <a name="remarks"></a>备注  
 此方法搜索全局符号注册表中的符号。  
  
## <a name="example"></a>示例  
  
```JavaScript  
// Local symbol  
var sym1 = Symbol("desc");  
// Global symbol  
var sym2 = Symbol.for("desc");  
  
console.log(Symbol.keyFor(sym1)):  
console.log(Symbol.keyFor(sym2));  
  
// Output:  
// undefined  
// desc  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]