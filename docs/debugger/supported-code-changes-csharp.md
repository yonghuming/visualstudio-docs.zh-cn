---
title: "受支持的代码更改 （C# 和 Visual Basic） |Microsoft 文档"
ms.custom: 
ms.date: 10/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a0a7d55b19455e22836d4750c0842a47816ee86
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="supported-code-changes-c-and-visual-basic"></a>受支持的代码更改 （C# 和 Visual Basic）
“编辑并继续”处理方法体内的大多数类型的代码更改。 但是，方法体外的大多数更改以及方法体内的小部分更改在调试期间不能应用。 若要应用这些不受支持的更改，你必须停止调试，重新开始新版本的代码。

## <a name="supported-changes-to-code"></a>支持的代码更改

下表显示可能会将所做的更改到 C# 和 Visual Basic 代码在调试会话期间无需重新启动会话。

|语言元素/功能|支持的编辑操作|限制|
|-|-|-|
|类型|添加方法、 字段、 构造函数、 et al|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|迭代器|添加或修改|No|
|异步/等待表达式|添加或修改|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|动态对象|添加或修改|No|
|Lambda 表达式|添加或修改|[是](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|LINQ 表达式|添加或修改|[Lambda 表达式相同](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> 编辑并继续通常支持较新的语言功能，如字符串内插和 null 条件运算符。 有关最新信息，请参阅[Enc 支持编辑](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)页。

## <a name="unsupported-changes-to-code"></a>不支持对代码的更改
 在调试会话期间，不向 C# 和 Visual Basic 代码应用下列更改：  
  
-   对当前语句或任何其他活动语句的更改。  
  
     活动语句包括为转至当前语句而调用过的任何语句（位于调用堆栈的函数中）。  
  
     当前语句在源窗口中以黄色背景标记。 其他活动语句以阴影背景标记，并且是只读的。 可以在更改这些默认颜色**选项**对话框。

- 下表显示对代码的更改不受支持的语言元素。

|语言元素/功能|不受支持的编辑操作|
|-|-|
|所有代码元素|重命名|
|命名空间|添加|
|命名空间、 类型、 成员|删除|
|泛型|添加或修改|
|接口|修改|
|类型|添加抽象或虚拟成员，添加重写 (请参阅[详细信息](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|类型|添加析构函数|
|成员|修改引用嵌入互操作类型的成员|
|成员 (Visual Basic)|修改与 On Error 或 Resume 语句一起使用的成员|
|成员 (Visual Basic)|修改包含的聚合、 Group By、 简单加入或组加入 LINQ 查询子句的成员|
|方法|修改签名|
|方法|通过添加的方法体使抽象方法成为非抽象|
|方法|删除方法体|
|特性|添加或修改|
|事件或属性|修改类型参数，基类型，则委托类型，或返回类型 |
|运算符或索引器|修改类型参数，基类型，则委托类型，或返回类型 |
|捕捉块|当它包含活动语句时，修改|
|try – catch – finally 块|当它包含活动语句时，修改|
|using 语句|添加|
|异步方法/lambda|修改异步方法/lambda 中面向.NET Framework 4 的项目，并减少 (请参阅[详细信息](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|迭代器|修改在面向.NET Framework 4 的项目中的迭代器，并减少 (请参阅[详细信息](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
  
## <a name="unsafe-code"></a>不安全代码  
 对不安全代码的更改具有与对安全代码的更改相同的限制，但它还包含一条附加限制：“编辑并继续”不支持对包含 `stackalloc` 运算符的方法内退出的不安全代码所作的更改。  

## <a name="unsupported-app-scenarios"></a>不受支持的应用方案

不受支持的应用程序和平台包括 ASP.NET 5、 Silverlight 5、 Windows Phone 和 Windows Phone 仿真程序和 Windows 8.1。

> [!NOTE]
> 支持的应用程序包含在 Windows 10 和面向.NET Framework 4.6 的 x86 和 x64 应用的 UWP 桌面或更高版本 （.NET Framework 是仅限桌面版本）。
  
## <a name="unsupported-scenarios"></a>不支持的方案  
 在以下调试方案中，“编辑并继续”不可用：  
  
-   混合模式（本机/托管）调试。  
  
-   SQL 调试。  
  
-   调试 Dr.Watson 转储。  
  
-   未处理的异常之后编辑代码时"**展开调用堆栈上未经处理的异常**"未选择选项。  
  
-   调试嵌入式运行时应用程序。  
  
-   调试应用程序中使用附加到进程 (**调试 > 附加到进程**) 而不是运行应用程序通过选择**启动**从**调试**菜单。  
  
-   调试优化后的代码。  
  
-   如果由于生成错误无法生成新版本的代码，则对旧版本的代码进行调试。
  
## <a name="see-also"></a>另请参阅  
 [编辑并继续 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [如何：使用“编辑并继续”(C#)](../debugger/how-to-use-edit-and-continue-csharp.md)