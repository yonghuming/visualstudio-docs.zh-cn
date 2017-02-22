---
title: "旧的语言服务分析器和扫描程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分析器，语言服务 [托管的包框架]"
  - "语言服务 [托管的包框架] 分析器"
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# 旧的语言服务分析器和扫描程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

分析器是语言服务的核心。 管理包框架 \(MPF\) 语言类需要一个语言分析器，以选择要显示的代码有关的信息。 分析器将文本分成词汇标记，然后确定这些令牌的类型和功能。  
  
## 讨论  
 下面是一个 C\# 方法。  
  
```c#  
namespace MyNamespace { class MyClass { public void MyFunction(int arg1) { int var1 = arg1; } } }  
```  
  
 在此示例中，令牌是单词和标点符号。 类型的标记如下所示。  
  
|标记名称|标记类型|  
|----------|----------|  
|命名空间类，公开的 void int|keyword|  
|\=|operator|  
|{ } \( \) ;|分隔符|  
|MyNamespace、 MyClass、 MyFunction、 arg1、 var1|identifier|  
|MyNamespace|namespace|  
|MyClass|类|  
|MyFunction|方法|  
|arg1|参数|  
|var1|本地变量|  
  
 分析器的作用是标识令牌。 某些令牌可以具有多个类型。 分析器确定令牌之后，信息以提供有用的功能，如语法突出显示，大括号匹配和 IntelliSense 操作可以使用该语言服务。  
  
## 类型的分析程序  
 语言服务分析器不用作同一编译器的一部分的分析器相同。 但是，这种类型的解析器需要同时使用扫描仪和分析器，编译器分析器的方式相同。  
  
-   扫描仪用于标识类型的令牌。 此信息用于语法突出显示和快速标识令牌类型可以触发其他操作，例如，大括号匹配。 由表示此扫描仪 <xref:Microsoft.VisualStudio.Package.IScanner> 接口。  
  
-   一个分析器用于描述函数和作用域的令牌。 此信息用于智能感知操作，以识别语言元素，如方法、 变量、 参数和声明，并提供成员和基于上下文的方法签名的列表。 此分析器还用于查找匹配的语言元素对，如大括号和括号。 通过访问此分析器 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 中的方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 类。  
  
 如何为您的语言服务中执行扫描仪和分析器是由您决定。 提供了几个资源，用于描述分析器的工作原理以及如何编写自己的分析器。 此外，有几种免费和商用产品，帮助创建一个分析器。  
  
### ParseSource 分析器  
 与作为编译器 \(在其中标记将转换为某种形式的可执行代码\) 的一部分使用的分析器，不同语言服务分析器可以多种不同原因，在许多不同的上下文中调用。 如何实现在这种方法 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 中的方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 类是由您决定。 务必要记住， <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 可能会在后台线程上调用方法。  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest> 结构包含对引用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 对象。 这 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 对象不能在后台线程中使用。 事实上，许多基本的 MPF 类不能在后台线程中使用。 其中包括 <xref:Microsoft.VisualStudio.Package.Source>, ，<xref:Microsoft.VisualStudio.Package.ViewFilter>, ，<xref:Microsoft.VisualStudio.Package.CodeWindowManager> 类，以及直接或间接与视图进行通信的任何其他类。  
  
 此分析器通常分析整个源文件第一次调用它或时分析原因值 <xref:Microsoft.VisualStudio.Package.ParseReason> 被授权者提供。 后续调用 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法处理的已分析的代码的一小部分，并可以通过使用以前的完全分析操作的结果更加迅速地执行。<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法来传递通过分析操作的结果 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 和 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 对象。<xref:Microsoft.VisualStudio.Package.AuthoringSink> 对象用于为特定的分析原因，例如，有关的信息范围的大括号或者具有的参数列表的方法签名中收集的信息。<xref:Microsoft.VisualStudio.Package.AuthoringScope> 提供的声明和方法签名以及支持集合有关转到高级编辑选项 \(**转到定义**, ，**转到声明**, ，**转到引用**\)。  
  
### IScanner 扫描仪  
 您还必须实现实现扫描仪 <xref:Microsoft.VisualStudio.Package.IScanner>。 但是，因为此扫描仪操作通过一行一行地逐个 <xref:Microsoft.VisualStudio.Package.Colorizer> 类，它是通常可以轻松地实现。 在每个行的开头，使 MPF <xref:Microsoft.VisualStudio.Package.Colorizer> 类用于传递给扫描程序的状态变量的值。 在每一行的末尾，扫描程序返回已更新的状态变量。 MPF 缓存的每一行此状态信息，以便扫描仪可以开始分析从任何行，而无需从源文件开头开始。 单个行此快速扫描允许编辑器向用户提供快速反馈。  
  
## 分析用于匹配大括号  
 此示例演示用于匹配用户键入一个右大括号的控制流。 在此过程中，用于着色的扫描程序还用于确定令牌和令牌是否可以触发匹配大括号操作的类型。 如果找到该触发器，则 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 调用方法来查找匹配的括号。 最后，将突出显示两个大括号。  
  
 即使在大括号中的触发器的名称使用和分析的原因，此过程不局限于实际的大括号。 支持的字符指定要匹配的对任何对。 示例包括 \(和\)，\<，\>，\[和\]。  
  
 假定的语言服务支持成对的大括号。  
  
1.  用户键入右花括号 \(}\)。  
  
2.  中的源文件中光标所在处插入的大括号和光标高级 1。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 中的方法 <xref:Microsoft.VisualStudio.Package.Source> 调用类使用的类型化的右大括号。  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法调用 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 中的方法 <xref:Microsoft.VisualStudio.Package.Source> 类来获取的令牌中就在当前光标位置之前的位置。 此令牌对应于类型化的右大括号\)。  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 方法调用 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法 <xref:Microsoft.VisualStudio.Package.Colorizer> 对象来获取当前行上的所有令牌。  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法调用 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> 方法 <xref:Microsoft.VisualStudio.Package.IScanner> 对象与当前行的文本。  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法将重复调用 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> 方法 <xref:Microsoft.VisualStudio.Package.IScanner> 对象从当前行中收集的所有令牌。  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 方法调用的私有方法 <xref:Microsoft.VisualStudio.Package.Source> 类来获取令牌，其中包含所需的位置，并从令牌列表中的阶段获得 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法。  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法查找令牌触发器标记为 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 从返回的令牌上 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 方法; 即，表示右大括号的令牌\)。  
  
6.  如果触发器标志 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 找到，则 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 中的方法 <xref:Microsoft.VisualStudio.Package.Source> 调用类。  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 方法开头的分析原因值的分析操作 <xref:Microsoft.VisualStudio.Package.ParseReason>。 此操作最终调用 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 类。 如果启用了异步分析，则此调用 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法在后台线程上发生。  
  
8.  在分析操作完成后，一个名为内部完成处理程序 \(也称为回调方法\) `HandleMatchBracesResponse` 中调用 <xref:Microsoft.VisualStudio.Package.Source> 类。 自动执行此调用 <xref:Microsoft.VisualStudio.Package.LanguageService> 基类，不是由分析器。  
  
9. `HandleMatchBracesResponse` 方法获取从范围列表 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 对象存储在 <xref:Microsoft.VisualStudio.Package.ParseRequest> 对象。 \(范围是一 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 结构，它在源文件中指定的行和字符范围。\) 此列表的范围通常包含两个范围，分别用于括号和右大括号。  
  
10. `HandleBracesResponse` 方法调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> 方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 对象存储在 <xref:Microsoft.VisualStudio.Package.ParseRequest> 对象。 它突出显示了给定的范围。  
  
11. 如果 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 属性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 启用，则 `HandleBracesResponse` 方法获取包含匹配范围的和在状态栏中显示该范围的前 80 个字符的文本。 这最适用于如果 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法包括附带对匹配的语言元素。 有关更多信息，请参见 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 属性。  
  
12. 完成操作。  
  
### 摘要  
 匹配的大括号操作是通常仅限于简单对语言元素。 更加复杂的元素，例如匹配三元组 \("`if(…)`"，"`{`"和"`}`"，或"`else`"，"`{`"和"`}`"\)，可以突出显示为单词自动完成操作的一部分。 例如，完成"else"一词后，匹配"`if`"语句可以突出显示。 如果有一系列 `if`\/`else if` 语句中，所有这些无法通过使用相同的机制作为匹配的括号突出显示。<xref:Microsoft.VisualStudio.Package.Source> 基类已支持此操作，请按以下方式: 扫描仪必须返回令牌的触发器值 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 触发器值合并在一起 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 在光标位置之前的标记。  
  
 有关更多信息，请参见[传统语言服务中的括号匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)。  
  
## 分析颜色设置  
 着色源代码非常简单，只需标识类型的令牌，将返回有关该类型的信息。<xref:Microsoft.VisualStudio.Package.Colorizer> 类用作编辑器和扫描仪，以提供有关每个标记的颜色信息之间的媒介。<xref:Microsoft.VisualStudio.Package.Colorizer> 类使用 <xref:Microsoft.VisualStudio.Package.IScanner> 对象以便于进行着色一行，并可以收集在源文件中的所有行的状态信息。 在 MPF 语言服务类中， <xref:Microsoft.VisualStudio.Package.Colorizer> 类没有需要重写，因为它与扫描仪通信只能通过 <xref:Microsoft.VisualStudio.Package.IScanner> 接口。 提供实现的对象 <xref:Microsoft.VisualStudio.Package.IScanner> 接口通过重写 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 类。  
  
 <xref:Microsoft.VisualStudio.Package.IScanner> 扫描仪被授权者提供一套通过源代码 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> 方法。 调用 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> 方法重复以获取行中的下一个令牌，直到行用尽的令牌。 有关着色、 MPF 视为行序列中添加所有源代码。 因此，扫描程序必须能够处理它即将作为行的源。 此外，任何时候，可以将任何行传递给扫描仪，只能保证，扫描程序会接收来自之前要扫描的行的行的状态变量。  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer> 类还用于确定令牌的触发器。 这些触发器告诉 MPF 特定标记可以启动更复杂的操作，例如单词自动完成或匹配的括号。 由于标识此类触发器必须快，并且必须在任何位置出现，扫描器，则最适合此任务。  
  
 有关详细信息，请参阅[在早期语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。  
  
## 分析针对功能和作用域  
 分析针对功能和作用域需要更多的工作比只识别的遇到的令牌类型。 分析器必须标识令牌类型，不仅能还用于对令牌的功能。 例如，标识符是只是一个名称，但您的语言标识符可能是类、 命名空间、 方法或变量，具体取决于上下文的名称。 常规类型的令牌可能是一个标识符，但标识符也可能具有其他含义，具体取决于它是什么以及其中定义。 此标识需要具有更广泛的了解正在分析的语言分析器。 这就是 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 类派上用场。<xref:Microsoft.VisualStudio.Package.AuthoringSink> 类收集有关标识符、 方法、 匹配的语言对 \(如大括号和括号\)，以及语言三元组的信息 \(与语言对类似，只是有三个部分，例如，"`foreach()`""`{`"和"`}`"\)。 此外，您可以重写 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 类，以支持用于早期的断点的验证，因此调试器不会加载，代码标识和 **自动** 调试窗口中，会自动显示局部变量和参数，如果程序正在调试，并且需要分析器以标识相应的本地变量和参数以外调试器可显示。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 作为的一部分将对象传递给分析器 <xref:Microsoft.VisualStudio.Package.ParseRequest> 对象和一个新 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 对象是每次创建一个新 <xref:Microsoft.VisualStudio.Package.ParseRequest> 创建对象。 此外， <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法必须返回 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 对象，用于处理各种智能感知操作。<xref:Microsoft.VisualStudio.Package.AuthoringScope> 对象维护声明的列表和列表的方法，或者其中将被填充，具体取决于用于分析的原因。<xref:Microsoft.VisualStudio.Package.AuthoringScope> 类必须实现。  
  
## 请参阅  
 [实现传统语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [旧的语言服务概述](../../extensibility/internals/legacy-language-service-overview.md)   
 [在早期语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [传统语言服务中的括号匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)