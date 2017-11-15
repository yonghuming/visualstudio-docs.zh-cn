---
title: "迭代器和生成器 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 68ef5b2f-0349-492b-b557-73ff2a2f90cf
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c27969609a38b87b15c727e9c8aef89ee77032
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iterators-and-generators-javascript"></a>迭代器和生成器 (JavaScript)
迭代器是一个对象，用于将容器对象作为列表遍历。 在 JavaScript 中，迭代器对象不是一个独立的内置对象，而是一个实现 `next` 方法以访问容器对象中的下一项的对象。  
  
 在 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] 中，可以创建自己的自定义迭代器。 但是，使用生成器通常会更加方便，它可以极大程度地简化迭代器的创建。 生成器是一种函数类型，该函数类型是迭代器的工厂。 要使用生成器函数创建自定义迭代器，请参阅[生成器](#Generators)。  
  
> [!CAUTION]
>  生成器在 [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] 中受到支持。  
  
## <a name="iterators"></a>迭代器  
 JavaScript 迭代器的实现涉及符合特定接口的两个或三个对象：  
  
-   Iterable 接口  
  
-   Iterator 接口  
  
-   IteratorResult 接口  
  
 可以使用这些接口创建自定义迭代器。 这让你能够使用 `for…of` 语句遍历可迭代对象。  
  
### <a name="iterable-interface"></a>Iterable 接口  
 Iterable 接口是可迭代对象（迭代器可以获得的对象）所需的接口。 例如，`for (let e of C)` 中的 `C` 必须实现 Iterable 接口。  
  
 可迭代对象必须提供 Symbol.iterator 方法，该方法会返回一个迭代器。  
  
```JavaScript  
obj[Symbol.iterator] = function() { return iterObj; }  
```  
  
 此属性必须是不接受任何参数并返回一个符合 `Iterator` 接口的对象 (`iterObject`) 的函数。  
  
 许多内置类型（包括数组）现在已可迭代。 `for…of` 循环使用可迭代对象。 （但是，并非所有内置可迭代对象都是迭代器。 例如，Array 对象本身不是迭代器，但它是可迭代的，而 ArrayIterator 也是可迭代的。）  
  
### <a name="iterator-interface"></a>Iterator 接口  
 Symbol.iterator 方法返回的对象必须实现 `next` 方法。 `next` 方法具有以下语法。  
  
```JavaScript  
iterObj.next() = function() { return iterResultObj; };  
```  
  
 `next` 方法是会返回一个值的函数。 该函数返回一个符合 `IteratorResult` 接口的对象 (`iterResultObj`)。 如果对迭代器的 `next` 方法的之前调用返回 `IteratorResult` 对象（其 `done` 属性为 true），则迭代终止且不会再调用 `next` 方法。  
  
 迭代器还可能包括 `return` 方法，以确保脚本用完迭代器后正确处理该迭代器。  
  
### <a name="iteratorresult-interface"></a>IteratorResult 接口  
 IteratorResult 接口是获得迭代器上 `next` 方法的结果所需的接口。 `next` 返回的对象必须提供 `done` 和 `value` 属性。  
  
```JavaScript  
var iterResultObj = { done: true|false, value: value }  
```  
  
 `done` 属性返回迭代器的 `next` 方法调用的状态，状态为 true 或 false。 如果已达到迭代器的末尾，则 `done` 返回 true。 如果未达到迭代器的末尾，则 `done` 返回 false，并有一个值可用。 如果 `done` 属性（其自己的属性或继承的属性）不存在，则 `done` 的结果被视为 false。  
  
 如果 `done` 为 false，则 `value` 属性返回当前迭代元素值。 如果 `done` 为 true，且如果提供了返回值，则这是迭代器的返回值。 如果迭代器不具有返回值，则未定义 `value`。 在这种情况下，如果符合对象没有继承显式值属性，则符合对象中可能不存在 `value` 属性。  
  
<a name="Generators"></a>   
## <a name="generators"></a>生成器  
 要轻松创建和使用自定义迭代器，请搭配使用 function* 语法和一个或多个 `yield` 表达式以创建一个生成器函数。 该生成器函数会返回一个迭代器（即生成器），该迭代器使生成器函数体能够执行。 函数执行到下一条 `yield` 或 `return` 语句。  
  
 调用迭代器的 `next` 方法以从生成器函数返回下一个值。  
  
 下面的示例演示为字符串对象返回迭代器的生成器。  
  
```JavaScript  
function* stringIter() {  
    var str = "bobsyouruncle";  
    var idx = 0;  
    while(idx < str.length)  
        yield str[idx++];  
}  
  
var si = stringIter();  
  
console.log(si.next().value);  
console.log(si.next().value);  
console.log(si.next().value);  
  
// Output:  
// b  
// o  
// b  
  
```  
  
 在生成器中，yield 操作数表达式终止对 `next` 的调用并返回具有两个属性（`done` (`done=false`) 和 `value` (`value=operand`)）的 `IteratorResult` 对象。 `operand` 是可选的，如果保留为空缺，则其值未定义。  
  
 在生成器中，通过返回具有 `done=true` 的 `IteratorResult` 以及 value 属性的可选操作数结果，`return` 语句可以终止生成器。  
  
 还可以使用 `yield*` 表达式替代 `yield`，以委托到另一个生成器或另一个可迭代对象，例如数组或字符串。  
  
 如果将下面的代码追加到前面的示例中，则 `yield*` 委托到 `stringIter` 生成器。  
  
```JavaScript  
function* strIter() {  
    yield "jo";  
    yield* stringIter();  
}  
  
var si2 = strIter();  
  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
  
// Output:  
// jo  
// b  
// o  
// b  
```  
  
 还可以将参数传递给 `next` 并使用该参数修改生成器的状态，以创建更高级的生成器。 `next` 将成为之前执行的 `yield` 表达式的结果值。 在下面的示例中，当你将值 100 传递给 `next` 方法时，会重置生成器的内部索引值。  
  
```  
function* strIter() {  
    var str = "jobob";  
    var idx = 0;  
    while(idx , str.length) {  
        var modify = yield str[idx++];  
        if(modify == 100) {  
            idx = 0;  
        }  
    }
}
  
var si3 = strIter();  
  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next(100).value);  
  
// Output:  
// j  
// o  
// b  
// j  
  
```  
  
 其他高级生成器可能调用生成器的 `throw` 方法。 引发的错误似乎会在生成器暂停的位置引发（在下一条 `yield` 语句之前）。
