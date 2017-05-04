---
title: "Windows 运行时类型的 JavaScript 表示形式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows 运行时类型 [JavaScript]"
  - "JavaScript，Windows 运行时类型"
ms.assetid: f4851802-8b40-4afa-ba6c-8a162a9a43cc
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Windows 运行时类型的 JavaScript 表示形式
下表描述了 JavaScript 表示 Windows 运行时类型的方式。  
  
> [!IMPORTANT]
>  Windows 运行时功能不可用于在 Internet Explorer 中运行的应用程序。  
  
## JavaScript 中的Windows 运行时类型  
  
|Windows 运行时 类型|JavaScript 表示形式|描述|  
|--------------------|---------------------|--------|  
|`UInt8`|`Number`|Windows 运行时 `Uint8` 是无符号 8 位整数，表示为 JavaScript 数字。  JavaScript 值首先转换为 JavaScript 数字，然后后面跟有 `ToUint32` 进程。  如果 JavaScript 数值是在 Uint8 范围之外，则结果将具有 2^8 中应用的模数。|  
|`Int32`|`Number`|Windows 运行时 `Int32` 是有符号 32 位整数，表示为 JavaScript 数字。  JavaScript 值首先转换为 JavaScript 数字，然后后面跟有 `ToInt32` 进程。  如果 JavaScript 数值是在 `Int32` 范围之外，则结果将具有 2^16 中应用的模数。|  
|`Int64`|`Number`|Windows 运行时 `Int64` 是一个有符号的 64 位整数，如果它属于该范围\[\- 2^53，2^53\]，则表示为一个标准编号。  如果它不在此范围内，则它表示为具有维护完整 64 位的整数数据的自定义后备存储的数值。  在这些自定义 Int64 数值上的所有算术运算将忽略该值转换为该范围的标准数字\[\- 2^53，2^53\]。  如果该值在此范围之外，则引发类型错误。  此转换过程的异常是 `==`、 `===`、 `SameValue`和 `RelationalComparison` 操作，当传递两个表示 64 位值时，比较基于完整 64 位的参数。  如果其中一个参数是一个标准 JavaScript 数字，则在比较之前这些操作还将参数转换为 JavaScript 数字。  如果它是 Int64 值，则 JavaScript 值将直接分配；否则将应用于传递给 Windows 运行时 的值的 `ToInteger` 转换的结果。  如果类型强制失败，将返回一个异常。|  
|`Uint64`|`Number`|Windows 运行时 `Uint64` 是一个无符号的 64 位整数，如果它属于该范围\[0，2^53\]，则表示为一个标准编号。  如果它不在此范围内，则它表示为具有维护完整 64 位的无符号整数数据的自定义后备存储的数字。  在这些自定义 Uint64 值上的所有算术运算将忽略该值转换为该范围的标准数字\[0，2^53\]。  如果该值在此范围之外，则引发类型错误。  此转换过程的异常是 `==`、 `===`、 `SameValue`和 `RelationalComparison` 操作，当传递两个 64 位值时，比较基于完整 64 位的参数。  如果其中一个参数是一个标准 JavaScript 数字，则在比较之前这些操作还将参数转换为 JavaScript 数字。  如果它是 Uint64 值，则 JavaScript 值将直接分配；否则将应用于传递给 Windows 运行时的值（后跟数模 2^52）的 `ToInteger` 转换的结果。  如果类型转换失败，将返回一个异常。|  
|`Single`|`Number`|Windows 运行时 `Single` 为 32 位浮点数，通过选择最接近的双精度值到单精度值表示为 JavaScript 数字。  JavaScript 值转换为 JavaScript 数字然后检查范围以确保该值在 32 位单精度 IEEE 浮点数 754 中可以表示。  如果转换或范围检查失败，则返回封送处理错误。|  
|`Double`|`Number`|Windows 运行时 `Double` 是 64 位浮点数。  `ToNumber` 用于将 Windows 运行时 `Double` 转换为 JavaScript 数字。  如果转换失败，则返回封送处理错误。|  
|`Boolean`|`Boolean`|Windows 运行时 `Boolean` 是零为 `false` 和零之外的任何值为 `true` 的 8 位值，表示为 JavaScript `Boolean`。  通过 `ToBoolean` JavaScript 值首先转换为 JavaScript `Boolean`。  这意味着 Windows 运行时函数声明为 `void func(BOOL);` 可以在 JavaScript 中编写为 `obj.func("test");`。  将使用 `BOOL` 参数作为 `TRUE` 传递来调用 Windows 运行时函数。  如果转换失败，则返回封送处理错误。|  
|`Char16`|`String`|Windows 运行时 `Char16` 是 16 位Unicode 字符，表示为包含单个字符的 JavaScript 字符串。  JavaScript 值转换为 JavaScript 字符串，通过 `ToString` 然后将检查以确保该字符串只有单个字符的长度。  然后传递单个字符为 `Char16` 值。  如果转换或长度检查失败，则返回封送处理错误。|  
|`String`|`String`|Windows 运行时 `String` 是 `Char16` 对象的不可变的序列。  字符串表示为 JavaScript `String` 对象。  Windows 运行时字符串没有 `null` 和空字符串\(""\)的不同的值。  `null` 和空字符串值将转换为 JavaScript 空字符串。  注意：在 JavaScript `null` 传递给需要字符串的 Windows 运行时参数时，将会导致字符串值“null”，非 `null` 或空字符串\(""\)。  传递给 Windows 运行时的字符串应始终实例化为空字符串。|  
|`Enumeration`|`Object`|Windows 运行时 `Enumeration` 是具有关联的命名常量的设置的 32 位整数（有符号或未签名）。  在 JavaScript 中，枚举表示为包含每个命名值的只读字段的对象。  枚举值转换为 JavaScript 数字如前面定义的 `Int32` 和 `UInt32`。  当 JavaScript 值转换为 Windows 运行时枚举时，它将转换、截断和范围检查如前面所述。  但是，该结果值未检查枚举中的指定的定义命名值。|  
|`Structure`|`Object`|Windows 运行时 `Structure` 是名为数据字段的异类集合。  在 JavaScript 中，结构表示为包含结构中的每个字段的命名属性的 JavaScript 对象。  如果任何结构值的转换失败，则返回封送处理错误。  在 JavaScript 对象中的字段没有等效在 Windows 运行时忽略的结构。  注意：Windows 运行时结构不能在 JavaScript 中与 `new` 关键字实例化。|  
|`Array`|`Array`|Windows 运行时 `Array` 将转换为 JavaScript 数组。  但是，Windows 运行时数组大小不可调，因此，不可能有某些 JavaScript 数组操作。  一个转换数组的内部 \[\[选件类\]\] 特性未设置“数组”，因为 ECMAScript 5 规范不允许。  这表示 `Array.isArray(v)` 返回 `false`。  JavaScript 值转换为 Windows 运行时数组如下所示：如果该值为 `null` 或 `undefined`，它将转换为本机 `null`。  如果其内部 \[\[选件类\]\] 属性为“数组”，则将其复制到本机数组，并传递此数组的引用。  如上文所述，如果它是一个转换的数组，则将传递基础本机数组。  注意：将 JavaScript 数组值传递给 Windows 运行方法产生该数组的完整副本。|  
|委托（函数回调）|`Function`|Windows 运行时委托是单个方法的引用。  Windows 运行时委托在 JavaScript 中表示为 JavaScript `Function`，确保在适当的线程上调用。  当调用 `Function` 时，参数转换为等效的 Windows 运行时参数类型。  如果 JavaScript 参数少于委托 `in` 参数，则委托调用失败。  如果 JavaScript 参数多于委托中的 `in` 参数，则忽略额外的 JavaScript 参数。  在调用委托之后，`out` 参数转换为 JavaScript 类型并返回。  如果本机 JavaScript 函数对象转换为 Windows 运行时委托，则在相应类型的 Windows 运行时委托中包装它。  在调用委托时，`in` 参数转换为 JavaScript 类型。  在调用委托后，返回值转换为委托的 `out` 参数。|  
|接口|`Object`|接口和接口组在 JavaScript 不直接表示为对象。  但是，接口表示作为参数并返回 Windows 运行时方法的类型。  按如下所示转换 Windows 运行时接口实例：<br /><br /> 1.  如果具有有效的运行时选件类，则将该对象表示为该选件类的实例。<br />2.  如果没有有效的运行时选件类，则将该对象表示为完全实现该实例已知道实现以及其所需接口的接口未命名的运行时的选件类的实例。<br /><br /> JavaScript 值测试以确定它是否是运行时选件类或接口的实例。  如果是，该原始的 Windows 运行时值实现该接口，则对象将传递给 Windows 运行时。|  
|运行时选件类|`Object`|在 Windows 运行时中的对象可以实现一个或多个接口的运行时选件类的实例。  Windows 运行时对象在 JavaScript 中表示为对象。  在所有选件类的实现接口上定义方法、属性和事件的联合在 JavaScript 对象的原型中表示命名属性。  JavaScript 使用者可以直接访问选件类的所有成员。  Windows 运行时对象包含运行时选件类的所有实现的接口中的所有成员的原型。|  
  
## 请参阅  
 [在 JavaScript 中使用 Windows 运行时](../jswinrt/using-the-windows-runtime-in-javascript.md)