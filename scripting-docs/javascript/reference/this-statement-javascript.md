---
title: "此语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: this_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- this statement
- constructors, referring to current object
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4afed1bd978d1985c151efa77873c93e699f0b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="this-statement-javascript"></a>this 语句 (JavaScript)
引用当前对象。  
  
## <a name="syntax"></a>语法  
  
```  
this.property  
```  
  
## <a name="remarks"></a>备注  
 必需的 `property` 参数是当前对象的属性之一。  
  
 `this` 关键字可在对象构造函数中用来引用当前对象。  
  
## <a name="example"></a>示例  
 在下面的示例中，**这**指的是新创建的 Car 对象，并将值分配给三个属性：  
  
```JavaScript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 **这**关键字通常引用**窗口**对象如果任何其他对象的范围之外使用。 但是，在事件处理程序内，`this` 引用引发事件的 DOM 元素。  
  
 在以下代码（针对 Internet Explorer 9 和更高版本）中，事件处理程序输出具有“clicker”ID 的按钮的字符串版本。  
  
```JavaScript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [使用 bind 方法](../../javascript/advanced/using-the-bind-method-javascript.md)