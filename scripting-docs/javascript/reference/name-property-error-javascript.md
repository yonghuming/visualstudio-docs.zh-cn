---
title: "name 属性 （错误） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: name
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Name property
- name property, error name
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a12157b4c467499fab23f7c4cb1be91e9ac5440
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="name-property-error-javascript"></a>name 属性（错误）(JavaScript)
返回的错误的名称。  
  
## <a name="syntax"></a>语法  
  
```  
  
errorObj.  
name  
  
```  
  
## <a name="parameters"></a>参数  
 `errorObj`  
 必需。 实例`Error`对象。  
  
## <a name="remarks"></a>备注  
 **名称**属性返回的错误的名称或异常类型。 运行时错误时，名称属性设置为以下的本机异常类型之一：  
  
|异常类型|含义|  
|--------------------|-------------|  
|ConversionError|试图将一个对象转换为不能转换的内容时，将出现此错误。|  
|RangeError|函数提供与已超出其允许的范围的自变量时，将出现此错误。 如果你尝试构造，例如，发生此错误`Array`对象不是有效的正整数的长度。|  
|ReferenceError|检测到无效的引用时发生此错误。 将出现此错误，例如，如果所需的引用是`null`。|  
|RegExpError|使用正则表达式编译错误时，将出现此错误。 正则表达式编译后，但是，不能出现此错误。 将发生此错误，例如，如果正则表达式声明使用了无效的语法，或标志以外的模式**我**， **g**，或**m**，或如果它包含相同的标志不止一次。|  
|SyntaxError|分析源文本和该不遵循正确的语法时，将出现此错误。 将出现此错误，例如，如果`eval`使用不是有效的程序文本的自变量调用函数。|  
|TypeError|操作数的实际类型与预期的类型不匹配时发生此错误。 发生此错误的一个示例是对内容进行不是对象或不支持调用的函数调用。|  
|URIError|检测到非法的统一资源标识符 (URI) 时，将出现此错误。 例如，这是错误字符串以找到非法字符，编码或解码时出现。|  
  
## <a name="example"></a>示例  
 下面的示例导致引发 TypeError 异常并显示错误和其消息的名称。  
  
```JavaScript  
try  
{  
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
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**:[错误对象](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [description 属性 （错误）](../../javascript/reference/description-property-error-javascript.md)   
 [message 属性 （错误）](../../javascript/reference/message-property-error-javascript.md)   
 [number 属性 (Error)](../../javascript/reference/number-property-error-javascript.md)