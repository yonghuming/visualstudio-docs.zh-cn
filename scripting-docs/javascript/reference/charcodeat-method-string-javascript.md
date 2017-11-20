---
title: "charCodeAt 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: charCodeAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: charCodeAt method
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e7b8e62dfd29aa42d9816d0c5e27cc90440751a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="charcodeat-method-string-javascript"></a>charCodeAt 方法 (String) (JavaScript)
返回位于指定位置处的字符的 Unicode 值。  
  
## <a name="syntax"></a>语法  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## <a name="parameters"></a>参数  
 `strObj`  
 必需。 任何`String`对象或字符串文本。  
  
 `index`  
 必需。 所需的字符的从零开始索引。 如果没有任何字符的指定索引处`NaN`返回。  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的示例演示 `charCodeAt` 方法的用法。  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [String.fromCharCode 函数](../../javascript/reference/string-fromcharcode-function-javascript.md)