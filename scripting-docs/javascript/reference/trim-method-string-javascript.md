---
title: "trim 方法 (String) (JavaScript) |Microsoft 文档"
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
helpviewer_keywords: trim method
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de358981cfbf569ef35be95b55b3e9856027df35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="trim-method-string-javascript"></a>trim 方法 (String) (JavaScript)
从字符串中移除前导空格、尾随空格和行终止符。  
  
## <a name="syntax"></a>语法  
  
```  
  
stringObj.trim()  
```  
  
## <a name="parameters"></a>参数  
 `stringObj`  
 必需。 `String` 对象或字符串。 `trim` 方法不修改该字符串。  
  
## <a name="return-value"></a>返回值  
 已移除前导空格、尾随空格和行终止符的原始字符串。  
  
## <a name="remarks"></a>备注  
 移除的字符包括空格、制表符、换页符、回车符和换行符。 请参阅[特殊字符](../../javascript/advanced/special-characters-javascript.md)有关空格和行终止符字符的完整列表。  
  
 有关演示如何实现剪裁方法示例，请参阅[原型和原型继承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示 `trim` 方法的用法。  
  
```JavaScript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [特殊字符](../../javascript/advanced/special-characters-javascript.md)   
 [字符串对象](../../javascript/reference/string-object-javascript.md)   
 [滚动、 平移和缩放示例应用](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)