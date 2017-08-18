---
title: "Windows 运行时类型的 JavaScript 表示形式 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Runtime types [JavaScript]
- JavaScript, Windows Runtime types
ms.assetid: f4851802-8b40-4afa-ba6c-8a162a9a43cc
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 8e4c21675d26bf857391d92b99b4a94637a761ca
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---
# <a name="javascript-representation-of-windows-runtime-types"></a>Windows 运行时类型的 JavaScript 表示形式
下表介绍了 JavaScript 表示 Windows 运行时类型的方式。  
  
> [!IMPORTANT]
>  Windows 运行时功能不适用于在 Internet Explorer 中运行的应用。  
  
## <a name="windows-runtime-types-in-javascript"></a>JavaScript 中的 Windows 运行时类型  
  
|Windows 运行时类型|JavaScript 表示形式|描述|  
|--------------------------|-------------------------------|-----------------|  
|`UInt8`|`Number`|Windows 运行时 `Uint8` 是一个 8 位无符号整数，表示为一个 JavaScript 数字。 JavaScript 值先转换为 JavaScript 数字，然后再执行 `ToUint32` 过程。 如果 JavaScript 数字超出 Uint8 的范围，结果将对 2^8 取模。|  
|`Int32`|`Number`|Windows 运行时 `Int32` 是一个 32 位带符号整数，表示为一个 JavaScript 数字。 JavaScript 值先转换为 JavaScript 数字，然后再执行 `ToInt32` 过程。 如果 JavaScript 数字超出 `Int32` 的范围，结果将对 2^16 取模。|  
|`Int64`|`Number`|Windows 运行时 `Int64` 是一个 64 位带符号整数，如果它在 [-2^53, 2^53] 范围内，则表示为一个标准数字。 如果它在此范围外，则会表示为一个具有保留完整 64 位整数数据的自定义后备存储的数值。 这些自定义 Int64 数值上的所有数学运算都会导致该值转换为 [-2^53, 2^53] 范围内的标准数字。 如果该值在此范围外，将引发类型错误。 此转换过程的异常是 `==`、`===`、`SameValue` 和 `RelationalComparison` 运算，当传递两个表示的 64 位值时，这些运算会基于完整 64 位对参数进行比较。 如果任一参数是一个标准 JavaScript 数字，则这些运算还会在进行比较之前，将参数转换为 JavaScript 数字。 如果是 Int64 值本身，则直接分配一个 JavaScript 值；否则，对该值应用 `ToInteger` 转换的结果会传递给 Windows 运行时。 如果类型强制转换失败，则返回异常。|  
|`Uint64`|`Number`|Windows 运行时 `Uint64` 是一个 64 位无符号整数，如果它在 [0, 2^53] 范围内，将表示为一个标准数字。 如果它在此范围外，则会表示为一个具有保留完整 64 位无符号整数数据的自定义后备存储的值。 这些自定义 Uint64 值上的所有数学运算都会导致值转换为 [0, 2^53] 范围内的标准数字。 如果该值在此范围外，将引发类型错误。 此转换过程的异常是 `==`、`===`、`SameValue` 和 `RelationalComparison` 运算，当传递两个 64 位值时，这些运算会基于完整 64 位对参数进行比较。 如果任一参数是一个标准 JavaScript 数字，则这些运算还会在进行比较之前，将参数转换为 JavaScript 数字。 如果是 Uint64 值本身，则直接分配一个 JavaScript 值；否则，对该值应用 `ToInteger` 转换，然后对 2^52 取模的结果会传递给 Windows 运行时。 如果类型转换失败，则返回异常。|  
|`Single`|`Number`|Windows 运行时 `Single` 是一个 32 位浮点数，通过选取与单精度值最接近的双精度值将其表示为一个 JavaScript 数字。 将 JavaScript 值转换为 JavaScript 数字，然后检查范围，以确保值可以表示为一个单精度 32 位 IEEE 754 浮点数。 如果转换或范围检查失败，则返回封送处理错误。|  
|`Double`|`Number`|Windows 运行时 `Double` 是 64 位浮点数。 `ToNumber` 用于将 Windows 运行时 `Double` 转换为 JavaScript 数字。 如果转换失败，则返回封送处理错误。|  
|`Boolean`|`Boolean`|Windows 运行时 `Boolean` 是一个 8 位值（其中，零为 `false`，任何非零值为 `true`），表示为一个 JavaScript `Boolean`。 JavaScript 值先由 `ToBoolean` 转换为 JavaScript `Boolean`。 这意味着，声明为 `void func(BOOL);` 的 Windows 运行时函数可以用 JavaScript 编写为 `obj.func("test");`。 Windows 运行时函数通过传递为 `TRUE` 的 `BOOL` 参数进行调用。 如果转换失败，则返回封送处理错误。|  
|`Char16`|`String`|Windows 运行时 `Char16` 是一个 16 位 Unicode 字符，表示为一个包含单个字符的 JavaScript 字符串。 JavaScript 值由 `ToString` 转换为 JavaScript 字符串，然后进行检查以确保字符串长度是否为单个字符。 然后，将单个字符作为 `Char16` 值进行传递。 如果转换或长度检查失败，则返回封送处理错误。|  
|`String`|`String`|Windows 运行时 `String` 是 `Char16` 对象的一个不可变序列。 字符串表示为 JavaScript `String` 对象。 Windows 运行时字符串为 `null` 和空字符串 ("") 提供相同的值。 `null` 和空字符串值将转换为 JavaScript 空字符串。 注意：当 JavaScript `null` 传递给需要字符串的 Windows 运行时参数时，它将生成字符串值“null”，而非 `null` 或空字符串 ("")。 应始终将传递给 Windows 运行时的字符串实例化为空字符串。|  
|`Enumeration`|`Object`|Windows 运行时 `Enumeration` 是一个有一组关联的命名常量的 32 位整数（带符号或无符号）。 在 JavaScript 中，枚举表示为一个包含每个命名值的只读字段的对象。 枚举值会转换为 JavaScript 数字，如之前对 `Int32` 和 `UInt32` 的定义。 当 JavaScript 值转换为一个 Windows 运行时枚举时，它会进行转换、截断和范围检查，如前所述。 但是，不会按照枚举中指定的定义的命名值检查生成的值。|  
|`Structure`|`Object`|Windows 运行时 `Structure` 是一个命名的数据字段的异类集合。 在 JavaScript 中，将结构表示为包含结构中每个字段的命名属性的 JavaScript 对象。 如果转换或任意结构值失败，则返回封送处理错误。 将忽略在 Windows 运行时结构中不具有等效项的 JavaScript 对象中的字段。 注意：不能通过 `new` 关键字在 JavaScript 中将 Windows 运行时结构实例化。|  
|`Array`|`Array`|Windows 运行时 `Array` 转换为 JavaScript 数组。 但是，Windows 运行时数组不可调整大小，因此不可能进行部分 JavaScript 数组运算。 由于 ECMAScript 5 规范不允许，因此，转换后数组的内部 [[Class]] 属性未设置为“Array”。 这表示 `Array.isArray(v)` 将返回 `false`。 JavaScript 值转换为 Windows 运行时数组，如下所示：如果值为 `null` 或 `undefined`，它将转换为本机 `null`。 如果它的内部 [[Class]] 属性为“Array”，则会将其复制到本机数组，并传递对该数组的引用。 如果是转换后的数组，如前所述，则将传递基础本机数组。 注意：将 JavaScript 数组值传递给 Windows 运行时方法会导致生成数组的完整副本。|  
|委托（函数回调）|`Function`|Windows 运行时委托是对单个方法的引用。 Windows 运行时委托在 JavaScript 中表示为 JavaScript `Function`，这可以保证在正确的线程上进行调用。 当调用 `Function` 时，参数会转换为等效的 Windows 运行时参数类型。 如果 JavaScript 实参少于委托 `in` 形参，则委托调用失败。 如果 JavaScript 实参多于委托中的 `in` 形参，则会忽略额外的 JavaScript 实参。 调用委托后，`out` 参数会转换为 JavaScript 类型，然后返回。 如果本机 JavaScript 函数对象转换为 Windows 运行时委托，则它会包装在相应类型的 Windows 运行时委托中。 调用委托时，`in` 参数会转换为 JavaScript 类型。 调用委托后，返回值会转换为该委托的 `out` 参数。|  
|接口|`Object`|接口和接口组不会直接在 JavaScript 中表示为对象。 但是，接口会表示为 Windows 运行时方法的参数和返回类型。 Windows 运行时接口实例转换如下所示：<br /><br /> 1.如果有有效的运行时类，则将对象表示为该类的实例。<br />2.如果没有有效的运行时类，则将对象表示为未命名运行时类的实例，该运行时类会准确实现该实例已为实现及其所需的接口所知的接口。<br /><br /> 测试 JavaScript 值以确定它是否为运行时类或接口的实例。 如果是，且原始 Windows 运行时值实现接口，则会将对象传递给 Windows 运行时。|  
|运行时类|`Object`|Windows 运行时中的对象可以是实现一个或多个接口的运行时类的实例。 Windows 运行时对象在 JavaScript 中表示为对象。 所有实现的类接口上定义的方法、属性和事件的并集表示 JavaScript 对象的原型中的命名属性。 JavaScript 使用者可以直接访问类的任意成员。 Windows 运行时对象具有包含运行时类的所有实现的接口中的所有成员的原型。|  
  
## <a name="see-also"></a>另请参阅  
 [在 JavaScript 中使用 Windows 运行时](../jswinrt/using-the-windows-runtime-in-javascript.md)
