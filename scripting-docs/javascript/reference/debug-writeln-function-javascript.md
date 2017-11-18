---
title: "Debug.writeln 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: writeln
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: writeIn method
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848760e59632b05605de2d73615a2b025df363da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugwriteln-function-javascript"></a>Debug.writeln 函数 (JavaScript)
将字符串发送到脚本调试程序后, 跟一个换行符。  
  
## <a name="syntax"></a>语法  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>参数  
 *str1，str2，...strN*  
 可选。 要将发送到脚本调试器的字符串。  
  
## <a name="remarks"></a>备注  
 `Debug.writeln`函数将字符串后, 跟一个换行符，则 Microsoft 脚本调试在运行时在即时窗口。 如果脚本未进行调试，`Debug.writeln`函数不起任何作用。  
  
 `Debug.writeln`函数是几乎与`Debug.write`函数。 唯一的区别是`Debug.write`函数不会发送字符串之后发送一个换行符。  
  
## <a name="example"></a>示例  
 此示例使用`Debug.writeln`函数在 Microsoft 脚本调试器的即时窗口中显示变量的值。  
  
> [!NOTE]
>  若要运行此示例，你必须安装脚本调试程序和脚本必须在调试模式下运行。  
>   
>  Internet Explorer 8 包括[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]调试器。 如果使用的是 Internet Explorer 的早期版本，请参阅 [如何：从 Internet Explorer 启用和启动脚本调试](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
```JavaScript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**: [Debug 对象](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [Debug.write 函数](../../javascript/reference/debug-write-function-javascript.md)