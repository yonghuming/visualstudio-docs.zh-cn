---
title: "错误对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Error
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Error object
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efc03f13a501a1a13a2e7f3eea000b406559f30b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="error-object-javascript"></a>Error 对象 (JavaScript)
包含有关错误的信息。  
  
## <a name="syntax"></a>语法  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## <a name="parameters"></a>参数  
 `errorObj`  
 必需。 `Error` 对象分配到的变量名称。 当你使用 `throw` 语句创建错误时，将省略变量赋值。  
  
 `number`  
 可选。 分配给错误的数值。 如果省略，则为零。  
  
 `description`  
 可选。 描述错误的简短字符串。 如果省略，则为空字符串。  
  
## <a name="remarks"></a>备注  
 每当出现运行时错误时，将创建一个 `Error` 对象实例来描述错误。 此实例具有两个内部属性，一个是包含错误描述的 `description` 属性，另一个是包含错误号的 `number` 属性。 有关详细信息，请参阅[JavaScript 运行时错误](../../javascript/reference/javascript-run-time-errors.md)。  
  
 错误号是一个 32 位值。 较高的 16 位字是设施代码，而较低的字是实际的错误代码。  
  
 可使用上面显示的语法显式创建 `Error` 对象，也可使用 `throw` 语句引发该对象。 在这两种情况下，你可以添加所选的任何属性来扩展 `Error` 对象的功能。  
  
 通常情况下，在中创建的本地变量**try … catch**语句是指隐式创建`Error`对象。 因此，你可以按所选的任何方式使用错误号和说明。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `Error` 对象的用法。  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## <a name="example"></a>示例  
 下面的示例阐释了隐式创建的 `Error` 对象的用法。  
  
```JavaScript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## <a name="methods"></a>方法  
 [toString 方法 （错误）](../../javascript/reference/tostring-method-error.md) &#124;[valueOf 方法 (Date)](../../javascript/reference/valueof-method-date.md)  
  
## <a name="properties"></a>属性  
 [constructor 属性 （错误）](../../javascript/reference/constructor-property-error.md) &#124;[description 属性](../../javascript/reference/description-property-error-javascript.md)&#124;[message 属性](../../javascript/reference/message-property-error-javascript.md)&#124;[name 属性](../../javascript/reference/name-property-error-javascript.md)&#124;[number 属性](../../javascript/reference/number-property-error-javascript.md)&#124;[prototype 属性 （错误）](../../javascript/reference/prototype-property-error.md) &#124;[stack 属性 （错误）](../../javascript/reference/stack-property-error-javascript.md) &#124;[stackTraceLimit 属性 （错误）](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [throw 语句](../../javascript/reference/throw-statement-javascript.md)   
 [try … catch...最后语句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [var 语句](../../javascript/reference/var-statement-javascript.md)   
 [Hilo JavaScript 示例应用程序 （Windows 应用商店）](http://hilojs.codeplex.com/SourceControl/latest)