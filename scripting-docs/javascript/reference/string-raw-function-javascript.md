---
title: "String.raw 函数 (JavaScript) |Microsoft 文档"
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
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53df2bf0e455da8b1ccc6de3cbf3f4e3ebee4c09
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="stringraw-function-javascript"></a>String.raw 函数 (JavaScript)
返回模板字符串的原始字符串形式。  
  
## <a name="syntax"></a>语法  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### <a name="parameters"></a>参数  
 `templateStr`  
 必需。 模板字符串。  
  
 `obj`  
 必需。 一个使用对象文字表示法指定的格式正确的对象，例如 { raw: “value” }。  
  
 `...substitutions`  
 可选。 数组 ( [rest 参数](../../javascript/functions-javascript.md)) 包含一个或多个替换值。  
  
## <a name="remarks"></a>备注  
 `String.raw`函数旨在用于[模板字符串](../../javascript/advanced/template-strings-javascript.md)。 原始字符串将包含存在于字符串中的任何转义字符和反斜杠。  
  
 如果 `obj` 不是格式正确的对象，则会引发错误。  
  
## <a name="example"></a>示例  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd   
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]