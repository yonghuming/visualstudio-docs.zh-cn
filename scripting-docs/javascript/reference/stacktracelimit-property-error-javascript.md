---
title: "stackTraceLimit 属性 （错误） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Error.stackTraceLimit
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error stack track limit [JavaScript]
- JavaScript error stack
- error stack [JavaScript]
- JavaScript stack trace limit
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af736ee8b385f93b761f1dfa021c23ee5376292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="stacktracelimit-property-error-javascript"></a>stackTraceLimit 属性（错误）(JavaScript)
获取或设置堆栈跟踪限制，它相当于要显示的错误帧数。 默认限制为 10。  
  
## <a name="syntax"></a>语法  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## <a name="remarks"></a>备注  
 你可以设置`stackTraceLimit`属性设置为任何正值设置介于 0 和`Infinity`。 如果`stackTraceLimit`属性设置为 0 时将引发错误时，显示没有堆栈跟踪。 如果该属性设置为负值或非数字值，则会将值转换为 0。 如果 stackTraceLimit 设置为`Infinity`，显示整个堆栈。 否则为`ToUint32`用于将值转换。  
  
## <a name="example"></a>示例  
 下面的示例演示如何设置并获取堆栈跟踪限制。  
  
```JavaScript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## <a name="requirements"></a>要求  
 支持的 Internet Explorer 10 中和在[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用。  
  
 **适用于**:[错误对象](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [description 属性 （错误）](../../javascript/reference/description-property-error-javascript.md)   
 [message 属性 （错误）](../../javascript/reference/message-property-error-javascript.md)   
 [name 属性 （错误）](../../javascript/reference/name-property-error-javascript.md)   
 [stack 属性 (Error)](../../javascript/reference/stack-property-error-javascript.md)