---
title: "normalize 方法 (String) (JavaScript) |Microsoft 文档"
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aece38339ea1ce8924f404938b2d35d07504d539
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="normalize-method-string-javascript"></a>normalize 方法 (String) (JavaScript)
返回指定字符串的 Unicode 范式。  
  
## <a name="syntax"></a>语法  
  
```  
stringObj.normalize([form]);  
```  
  
#### <a name="parameters"></a>参数  
 `stringObj`  
 必需。 要对照测试的字符串对象。  
  
 `form`  
 可选。 Unicode 范式值。  
  
## <a name="return-value"></a>返回值  
 指定字符串的 Unicode 范式。  
  
## <a name="exceptions"></a>异常  
 如果 `form` 是不受支持的值，则会引发 `RangeError`。  
  
## <a name="remarks"></a>备注  
 如果 `stringObj` 不是字符串，则它将被转换为字符串（在方法尝试返回该字符串的 Unicode 范式之前）。  
  
 `form`必须一个 Unicode 范式值，"NFC"、"NFD"、"NFKC"或"NFKD"，对应于为指定的值[Unicode 标准附录 #15](http://www.unicode.org/reports/tr15/)。 `form` 的默认值为“NFC”。  
  
## <a name="example"></a>示例  
 下面的代码示例演示 `normalize` 方法的使用。  
  
```JavaScript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]