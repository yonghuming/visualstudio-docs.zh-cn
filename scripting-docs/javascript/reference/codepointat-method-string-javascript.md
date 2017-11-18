---
title: "codePointAt 方法 (String) (JavaScript) |Microsoft 文档"
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd5ef17db177dfb1d532bfb88d1d0d77cdb7304
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="codepointat-method-string-javascript"></a>codePointAt 方法（字符串）(JavaScript)
返回一个 Unicode utf-16 字符的码位。  
  
## <a name="syntax"></a>语法  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### <a name="parameters"></a>参数  
 `stringObj`  
 必需。 字符串对象。  
  
 `pos`  
 必需。 字符的位置。  
  
## <a name="remarks"></a>备注  
 此方法返回所有 UTF-16 字符的码位值，包括 astral 码位（具有四个以上的十六进制值的码位）。  
  
 如果 `pos` 小于零 (0) 或大于字符串大小，则返回值为 `undefined`。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `codePointAt` 方法。  
  
```JavaScript  
var cp1 = "𠮷".codePointAt(0);  
var cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98   
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
