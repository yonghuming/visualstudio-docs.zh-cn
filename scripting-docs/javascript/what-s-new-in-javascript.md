---
title: "JavaScript 的新增功能 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 342b68ef-df93-48c4-81de-bdf6b6ce58d9
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 540d10958a7f2d406a6d70a633fc09a2cada8f41
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---
# <a name="what39s-new-in-javascript"></a>JavaScript 的新增功能
本文档列出了同时在[边缘模式](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx)、[!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] 和 Windows Phone 应用商店应用中受支持的 JavaScript 的新功能。  
  
 要找出哪些 JavaScript 元素在边缘模式中受支持，但在 [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] 应用中已弃用，请参阅[版本信息](../javascript/reference/javascript-version-information.md)。  
  
> [!IMPORTANT]
>  有关如何使用 JavaScript 创建 [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] 和 Windows Phone 应用商店应用的信息，包括有关 Visual Studio JavaScript 编辑器和其他功能的信息，请参阅[使用 Visual Studio 2013 开发 Windows 应用商店应用](http://go.microsoft.com/fwlink/p/?LinkID=238263)。  
  
## <a name="new-features-in-javascript"></a>JavaScript 中的新功能  
  
|功能|描述|  
|-------------|-----------------|  
|类|新语法支持[类](../javascript/reference/class-statement-javascript.md)的声明。|  
|承诺|通过[承诺](../javascript/reference/promise-object-javascript.md)可以实现更轻松、更干净的异步编码。 支持承诺构造函数，以及 `all` 和 `race` 实用工具方法。|  
|迭代器|现在可以循环访问可迭代对象（包括数组、类似数组的对象和迭代器），从而使用要对每个非重复属性的值执行的语句来调用自定义迭代挂钩。 有关详细信息，请参阅[迭代器和生成器](../javascript/advanced/iterators-and-generators-javascript.md)。 **注意：**尚不支持生成器。|  
|箭头函数|箭头函数 (=>) 为采用词法 `this` 绑定的 `function` 关键字提供速记形式语法。|  
|用于内置对象的新方法|[Array 对象](../javascript/reference/array-object-javascript.md)、[Math 对象](../javascript/reference/math-object-javascript.md)、[Number 对象](../javascript/reference/number-object-javascript.md)、[Object 对象](../javascript/reference/object-object-javascript.md)和 [String 对象](../javascript/reference/string-object-javascript.md)内置对象包括许多用于操作和检测数据的新实用工具函数和属性。|  
|对象文字增强功能|对象现在针对其值初始化为同名变量的属性支持计算属性、简洁方法定义和速记形式语法。 有关详细信息，请参阅[创建对象](../javascript/creating-objects-javascript.md)。|  
|代理|[代理](../javascript/reference/proxy-object-javascript.md)可实现对象的自定义行为。|  
|Rest 参数|通过 Rest 参数可以将函数调用中的连续自变量转换为数组。 有关详细信息，请参阅[函数](../javascript/functions-javascript.md)。|  
|Spread 运算符|[spread 运算符](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) (`...`) 将可迭代表达式扩展为各个自变量。 例如，`a.b(...array)` 与 `a.b.apply(a, array)` 近似相同。|  
|符号|[符号](../javascript/reference/symbol-object-javascript.md)对象允许将属性添加现有对象，而不可能干扰现有对象属性、不存在任何意外的可见性并且不存在其他代码进行的任何其他不协调添加。|  
|模板字符串|[模板字符串](../javascript/advanced/template-strings-javascript.md)是允许要进行计算并与字符串连接的表达式使用的字符串。|  
|Unicode 增强功能|对 Unicode 支持进行了改进。 例如，一种新的转义序列格式支持 astral 码位（包含四个以上十六进制数字的码位）。 有关详细信息，请参阅[特殊字符](../javascript/advanced/special-characters-javascript.md)。|  
|WeakSet|[WeakSet](../javascript/reference/weakset-object-javascript.md) 是未在任何其他位置引用时将进行垃圾回收的对象的集合。|  
  
## <a name="see-also"></a>另请参阅  
 [JavaScript 语言参考](../javascript/javascript-language-reference.md)
