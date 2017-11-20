---
title: "message 属性 （错误） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: message
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Message property
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dbd2db6c6d31dc48d90c3b07d2388eacf73ae7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="message-property-error-javascript"></a>message 属性（错误）(JavaScript)
返回一个错误消息字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
errorObj.message  
```  
  
## <a name="parameters"></a>参数  
 `errorObj`  
 必需。 实例`Error`对象。  
  
## <a name="remarks"></a>备注  
 `message`属性返回一个字符串，包含与特定错误关联的错误消息。  
  
 `description`和`message`属性提供相同的功能。 `description`属性提供了后向兼容性;`message`属性符合 ECMA 标准。  
  
## <a name="example"></a>示例  
 下面的示例导致引发 TypeError 异常并显示错误和其消息的名称。  
  
```JavaScript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>示例  
 此代码的输出如下所示。  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **适用于**:[错误对象](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [description 属性 （错误）](../../javascript/reference/description-property-error-javascript.md)   
 [name 属性 (Error)](../../javascript/reference/name-property-error-javascript.md)