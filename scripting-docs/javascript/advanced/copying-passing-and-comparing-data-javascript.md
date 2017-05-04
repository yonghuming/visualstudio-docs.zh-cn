---
title: "复制、传递和比较数据 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "数组 [Visual Studio], 复制数据"
  - "数组 [Visual Studio], 传递值"
  - "数组 [Visual Studio], 设置数据类型"
  - "ByRef 参数"
  - "ByVal 参数"
  - "函数参数"
  - "函数参数, 关于函数参数"
  - "字符串比较"
  - "字符串比较, 测试数据"
ms.assetid: fbccd877-7249-45d4-bd9f-6bcd8ba94a6b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 复制、传递和比较数据 (JavaScript)
在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中，数据的处理方式取决于其数据类型。  
  
## 按值与按引用  
 数字和布尔值（**true** 和 **false**）按值进行复制、传递和比较。  按值进行复制或传递时，将在计算机内存中分配一个空间，然后将原始项的值复制到该空间中。  如果随后更改原始项，也不影响副本（反之亦然），因为两者是各自不同的实体。  
  
 对象、数组和函数按引用进行复制、传递和比较。  按引用进行复制或传递时，实质上创建原始项的指针，并像副本一样使用该指针。  如果随后更改原始项，则同时更改原始项和副本（反之亦然）。  实际上只有一个实体；“副本”实际上不是副本，而只是对数据的另一个引用。  
  
 按引用进行比较时，两个变量必须恰好引用同一个实体，才能成功进行比较。  例如，两个不同 **Array** 对象比较之后的结果始终为不等，即使二者所含的元素相同也是如此。  若要使比较成功，其中一个变量必须是对另一个变量的引用。  若要检查两个数组是否包含相同的元素，请比较 **toString\(\)** 方法的结果。  
  
 最后，字符串按引用进行复制和传递，但按值进行比较。  注意，如果有两个 **String** 对象（用 **new** String\("something"\) 创建），则按引用进行比较，但是，如果其中一个值为或两个值均为字符串值，则按值进行比较。  
  
> [!NOTE]
>  由于 ASCII 和 ANSI 字符集的构造方式，因此在序列顺序中大写字母排在小写字母之前。  例如，“Zoo”相比之下*小于*“aardvark”。如果要执行不区分大小写的匹配，则可以对两个字符串调用 **toUpperCase\(\)** 或 **toLowerCase\(\)**。  
  
## 将参数传递给函数  
 按值将参数传递给某个函数时，将会创建该参数的单独副本（一个仅存在于该函数内部的副本）。  即使按引用传递对象和数组，如果在该函数中用一个新值直接覆盖它们，则在该函数之外也不会反映新值。  只有对对象属性或数组元素的更改才会在函数外可见。  
  
 例如（使用 Internet Explorer 对象模型）：  
  
```javascript  
// This clobbers (over-writes) its parameter, so the change  
// is not reflected in the calling code.  
function Clobber(param)   
{  
    // clobber the parameter; this will not be seen in   
    // the calling code  
    param = new Object();  
    param.message = "This will not work";  
}  
  
// This modifies a property of the parameter, which  
// can be seen in the calling code.  
function Update(param)  
{  
    // Modify the property of the object; this will be seen  
    // in the calling code.  
    param.message = "I was changed";  
}  
  
// Create an object, and give it a property.  
var obj = new Object();  
obj.message = "This is the original";  
  
// Call Clobber, and print obj.message. Note that it hasn't changed.  
Clobber(obj);  
window.alert(obj.message); // Still displays "This is the original".  
  
// Call Update, and print obj.message. Note that is has changed.  
Update(obj);  
window.alert(obj.message); // Displays "I was changed".  
```  
  
## 测试数据  
 执行按值测试时，将比较两个不同的项，以查看其是否彼此相等。  通常，这种比较是逐字节进行的。  按引用测试时，将检查两项是否为指向同一个原始项的指针。  如果是，则其比较结果为相等；否则，即使其值完全相同（逐字节），其比较结果仍为不相等。  
  
 按引用复制和传递字符串可节省内存；但是，由于字符串一经创建即无法更改，因此可按值比较字符串。  这样可测试两个字符串的内容是否相同，即使其中一个是完全独立于另一个生成的也是如此。  
  
## 请参阅  
 [计算日期和时间 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)