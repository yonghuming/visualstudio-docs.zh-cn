---
title: "repeat 方法 (String) (JavaScript) |Microsoft 文档"
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1a3d6edce877a97b0e46a69c43b667231c26981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="repeat-method-string-javascript"></a>repeat 方法（字符串）(JavaScript)
返回一个新的字符串对象，它的值等于重复了指定次数的原始字符串。  
  
## <a name="syntax"></a>语法  
  
```  
stringObj.repeat(count);  
```  
  
#### <a name="parameters"></a>参数  
 `stringObj`  
 必需。 字符串对象。  
  
 `count`  
 必需。 返回字符串中原始字符串重复的次数。  
  
## <a name="exceptions"></a>异常  
 当且仅当该自变量为负或正无穷时，此方法才引发 RangeError。  
  
## <a name="remarks"></a>备注  
 `repeat` 方法将原始字符串串联到新字符串，串联次数由 `count` 指定。  
  
 如果 `count` 不是小于 `Infinity` 的正数，则此方法将引发错误。  
  
## <a name="example"></a>示例  
  
```JavaScript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]