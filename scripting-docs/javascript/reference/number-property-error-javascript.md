---
title: "number 属性 （错误） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Number
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Number property
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbc229e7d0572e1a3dbed056b344da7ff9ce7292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="number-property-error-javascript"></a>number 属性（错误）(JavaScript)
返回或设置与特定错误关联的数字值。 `Error`对象的默认属性是**数**。  
  
## <a name="syntax"></a>语法  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## <a name="parameters"></a>参数  
 *对象*  
 任何实例`Error`对象。  
  
 *错误号*  
 一个整数，表示出错。  
  
## <a name="remarks"></a>备注  
 错误号是一个 32 位值。 较高的 16 位字是设施代码，而较低的字为错误的代码。 若要确定错误代码，请使用`&`(按位和) 运算符的十六进制数与组合数属性`0xFFFF`。  
  
## <a name="example"></a>示例  
 下面的示例导致引发异常，并显示错误数目派生的错误代码。  
  
```JavaScript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## <a name="example"></a>示例  
 此代码的输出如下所示。  
  
```JavaScript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **适用于**:[错误对象](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [description 属性 （错误）](../../javascript/reference/description-property-error-javascript.md)   
 [message 属性 （错误）](../../javascript/reference/message-property-error-javascript.md)   
 [name 属性 (Error)](../../javascript/reference/name-property-error-javascript.md)