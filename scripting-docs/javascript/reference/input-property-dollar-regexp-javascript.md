---
title: "input 属性 ($_) (RegExp) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: $_
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- input property
- $_ property
ms.assetid: 88c6d1d8-56f7-4334-a7eb-e899aec9cda4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a447950783473d975bfe799eaa2bf18008e539e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="input-property--regexp-javascript"></a>input 属性 ($_) (RegExp) (JavaScript)
返回对其执行正则表达式搜索字符串。 只读。  
  
## <a name="syntax"></a>语法  
  
```  
  
RegExp.input  
```  
  
## <a name="remarks"></a>备注  
 此属性与关联的对象始终是全局`RegExp`对象。  
  
 值**输入**的随时更改搜索的字符串，则修改属性。  
  
 下面的示例演示如何使用**输入**属性：  
  
```JavaScript  
function inputDemo(){  
   var s;  
   var re = new RegExp("d(b+)(d)","ig");  
   var str = "cdbBdbsbdbdz";  
   var arr = re.exec(str);  
   s = "The string used for the match was " + RegExp.input;   
   return(s);  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**: [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)