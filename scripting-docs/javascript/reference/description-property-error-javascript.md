---
title: "description 属性 （错误） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Description
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, error description
- Description property
- errors, description
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6135951fdf65698ed48b9bbacdcc55c1aac22d41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="description-property-error-javascript"></a>description 属性（错误）(JavaScript)
返回或设置与特定错误关联的描述性字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## <a name="parameters"></a>参数  
 *对象*  
 必需。 任何实例`Error`对象。  
  
 `stringExpression`  
 可选。 包含错误的说明的字符串表达式。  
  
## <a name="remarks"></a>备注  
 **说明**属性包含与特定错误关联的错误消息字符串。 使用此属性中包含的值错误向用户发出警报。  
  
 **说明**和**消息**属性提供相同的功能;**说明**属性提供向后兼容性; **消息**属性符合 ECMA 标准。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**说明**属性。  
  
```JavaScript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **适用于**:[错误对象](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [number 属性 （错误）](../../javascript/reference/number-property-error-javascript.md)   
 [message 属性 （错误）](../../javascript/reference/message-property-error-javascript.md)   
 [name 属性 (Error)](../../javascript/reference/name-property-error-javascript.md)