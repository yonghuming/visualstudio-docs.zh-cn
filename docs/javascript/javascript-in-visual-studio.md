---
title: "Visual Studio 中的 JavaScript | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 77e7ce26df70e41e2328442454fe78c7a663f1f3
ms.openlocfilehash: de00ef86413571739446b61427c3a8e6c4680c06
ms.lasthandoff: 03/08/2017

---
# <a name="javascript-in-visual-studio"></a>Visual Studio 中的 JavaScript
JavaScript 是 Visual Studio 中的一级语言。 当你在 Visual Studio IDE 中编写 JavaScript 代码时，你可以使用该标准编辑帮助（代码片段，IntelliSense 等等）的大部分或全部。 对于许多应用程序类型和服务，可以编写 JavaScript 代码。  
  
 有关 JavaScript 语言参考文档，请参阅 [JavaScript](https://docs.microsoft.com/scripting/javascript/javascript-language-reference)。
  
 可能需要特定版本的 Visual Studio 或特定 Visual Studio 扩展来使用 HTML 和 JavaScript 开发特定应用程序类型和服务。 下面的列表包含指向详细信息的链接。  
  
-   若要使用 Apache Cordova 创建跨平台的应用，请参阅 [Visual Studio Tools for Apache Cordova](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/)。  
  
-   有关 Visual Studio 中可使用的 JavaScript 技术的链接，请参阅 [JavaScript](https://docs.microsoft.com/scripting/javascript/) 和 [Scripting Technologies](https://docs.microsoft.com/scripting/)（脚本编写技术）页。
  
 Visual Studio 中的 JavaScript 编辑器提供 IntelliSense 支持。 有关详细信息，请参阅 [JavaScript IntelliSense](../ide/javascript-intellisense.md)。  
  
## <a name="whats-new-in-javascript"></a>JavaScript 的新增功能  
 下表列出了 JavaScript 的新增功能。  
  
|功能|描述|  
|-------------|-----------------|  
|类|新语法支持[类](http://msdn.microsoft.com/Library/bf45ebad-4678-4062-88df-55d32b603c69)的声明。|  
|承诺|通过[承诺](http://msdn.microsoft.com/Library/358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6)可以实现更轻松、更干净的异步编码。 支持承诺构造函数，以及 `all` 和 `race` 实用工具方法。|  
|迭代器|现在可以循环访问可迭代对象（包括数组、类似数组的对象和迭代器），从而使用要对每个非重复属性的值执行的语句来调用自定义迭代挂钩。 有关详细信息，请参阅[迭代器和生成器](http://msdn.microsoft.com/Library/68ef5b2f-0349-492b-b557-73ff2a2f90cf)。 **注意：**尚不支持生成器。|  
|箭头函数|箭头函数 (=>) 为采用词法 `this` 绑定的 `function` 关键字提供速记形式语法。|  
|用于内置对象的新方法|[Array 对象](http://msdn.microsoft.com/Library/08e5f552-0797-4b48-8164-609582fc18c9)、[Math 对象](http://msdn.microsoft.com/Library/607b94cb-921c-43cd-b514-fdbc13aeced6)、[Number 对象](http://msdn.microsoft.com/Library/76e87c37-cf6c-46cc-bafa-04be1fe3d78d)、[Object 对象](http://msdn.microsoft.com/Library/d24ef8fc-217b-4828-94e1-19f72780bae0)和 [String 对象](http://msdn.microsoft.com/Library/8063ecd5-5778-4e87-b985-b21420171914)内置对象包括许多用于操作和检测数据的新实用工具函数和属性。|  
|对象文字增强功能|对象现在针对其值初始化为同名变量的属性支持计算属性、简洁方法定义和速记形式语法。 有关详细信息，请参阅[创建对象](http://msdn.microsoft.com/Library/58d1baa5-4fe8-4a56-a926-5b11765df704)。|  
|代理|[代理](http://msdn.microsoft.com/Library/2b89abee-04fa-47e6-9676-980016cff5f8)可实现对象的自定义行为。|  
|Rest 参数|通过 Rest 参数可以将函数调用中的连续自变量转换为数组。 有关详细信息，请参阅[函数](http://msdn.microsoft.com/Library/e2a72b5a-3edd-43d8-95e8-91721b38c1c1)。|  
|Spread 运算符|[spread 运算符](http://msdn.microsoft.com/Library/10263a4c-bd27-4d87-9917-fb4b6bf373db) (`…`) 将可迭代表达式扩展为各个自变量。 例如，`a.b(…array)` 与 `a.b.apply(a, array)` 近似相同。|  
|符号|[符号](http://msdn.microsoft.com/Library/2ad059f1-4b7f-4758-882a-c74ce1283ab0)对象允许将属性添加现有对象，而不可能干扰现有对象属性、不存在任何意外的可见性并且不存在其他代码进行的任何其他不协调添加。|  
|模板字符串|[模板字符串](http://msdn.microsoft.com/Library/f2e525a5-b0fc-49c3-95a0-641788e5c12a)是允许要进行计算并与字符串连接的表达式使用的字符串。|  
|Unicode 增强功能|对 Unicode 支持进行了改进。 例如，一种新的转义序列格式支持 astral 码位（包含四个以上十六进制数字的码位）。 有关详细信息，请参阅[特殊字符](http://msdn.microsoft.com/Library/3b38b1bd-1f0f-4748-b13e-55cab36fd126)。|  
|WeakSet|[WeakSet](http://msdn.microsoft.com/Library/f97e6e7c-d678-4e32-978e-d949a7cafa3a) 是未在任何其他位置引用时将进行垃圾回收的对象的集合。|
