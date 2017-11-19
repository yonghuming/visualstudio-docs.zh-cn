---
title: "旧语言服务分析器和扫描程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30453237dcd95607a4f3524f115d16bc1cf4859a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-parser-and-scanner"></a>旧语言服务分析器和扫描程序
分析器是语言服务的核心。 托管包框架 (MPF) 语言类需要的语言分析程序，可以选择要显示的代码的相关信息。 分析器将文本分隔为词法令牌，然后确定这些令牌的类型和功能。  
  
## <a name="discussion"></a>讨论  
 以下是 C# 方法。  
  
```csharp  
namespace MyNamespace  
{  
    class MyClass  
    {  
        public void MyFunction(int arg1)  
        {  
            int var1 = arg1;  
        }  
    }  
}  
```  
  
 在此示例中，令牌是单词和标点符号。 类型的标记如下所示。  
  
|标记名称|标记类型|  
|----------------|----------------|  
|命名空间、 类，公开的 void、 int|keyword|  
|=|operator|  
|{ } ( ) ;|分隔符|  
|MyNamespace、 MyClass、 MyFunction、 arg1、 var1|identifier|  
|MyNamespace|namespace|  
|MyClass|类|  
|MyFunction|方法|  
|arg1|参数|  
|var1|本地变量|  
  
 分析器的角色是标识令牌。 某些令牌可以具有多个类型。 分析器确定令牌之后，可以使用语言服务，可提供有用的功能，如语法突出显示，大括号匹配，信息和智能感知操作。  
  
## <a name="types-of-parsers"></a>类型的分析器  
 语言服务分析器不用作编译器的一部分的分析器相同。 但是，这种类型的分析器需要使用扫描仪和分析器中，编译器分析器的方式相同。  
  
-   扫描程序用于标识令牌类型。 此信息用于语法突出显示和快速标识令牌类型可触发其他操作，例如，大括号匹配。 此扫描程序都由<xref:Microsoft.VisualStudio.Package.IScanner>接口。  
  
-   分析器用于描述函数和作用域的令牌。 若要标识语言元素，如方法、 变量、 参数和声明，并提供成员和基于上下文在方法签名的列表，将在 IntelliSense 操作中使用此信息。 此分析器还用于查找匹配的语言元素对，如大括号和括号。 通过访问此分析器<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>类。  
  
 如何为你的语言服务中实现扫描仪和分析器是由您决定。 提供了多个资源，用于描述分析器的工作原理以及如何编写你自己的分析程序。 同样，有好几种免费的商业产品可显示的帮助创建一个分析器。  
  
### <a name="the-parsesource-parser"></a>ParseSource 分析器  
 与用作的编译器 （其中标记将转换为某种形式的可执行代码） 的一部分的分析器，不同语言服务分析器可以因多种不同原因以及在许多不同的上下文中调用。 如何实现此方法在<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>类是由您决定。 务必要记住的<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>可能会在后台线程上调用方法。  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest>结构包含对引用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>对象。 这<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>对象不在后台线程中使用。 事实上，许多基本的 MPF 类不能在后台线程。 其中包括<xref:Microsoft.VisualStudio.Package.Source>， <xref:Microsoft.VisualStudio.Package.ViewFilter>，<xref:Microsoft.VisualStudio.Package.CodeWindowManager>类和任何直接或间接通信与视图的其他类。  
  
 此分析器通常分析整个源文件第一个时间就是或分析时原因值<xref:Microsoft.VisualStudio.Package.ParseReason>提供。 后续调用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法处理已分析的代码的一小部分，并可通过使用以前的完整分析操作的结果更快速地执行。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法传递通过在分析操作的结果<xref:Microsoft.VisualStudio.Package.AuthoringSink>和<xref:Microsoft.VisualStudio.Package.AuthoringScope>对象。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>对象用于收集特定的分析原因，例如，范围的信息匹配大括号或具有参数列表的方法签名的信息。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>提供的声明和方法签名以及支持集合为转到高级编辑选项 (**转到定义**，**转到声明**，**转到引用**)。  
  
### <a name="the-iscanner-scanner"></a>IScanner 扫描程序  
 你还必须实现一种扫描仪实现<xref:Microsoft.VisualStudio.Package.IScanner>。 但是，因为此扫描程序操作通过一行一行地基于<xref:Microsoft.VisualStudio.Package.Colorizer>类，它是通常更加轻松地实现。 在每个行的开头，MPF 使<xref:Microsoft.VisualStudio.Package.Colorizer>类用于为传递给扫描仪一个状态变量的值。 在每个行的末尾，扫描程序返回更新的状态变量。 MPF 缓存每个行的此状态信息，以便扫描程序可以开始分析从任何行，而无需在源代码文件的开头处开始。 此快速扫描的单个行允许向用户提供快速反馈编辑器。  
  
## <a name="parsing-for-matching-braces"></a>分析为匹配大括号  
 此示例演示用于匹配用户已键入右大括号的控制流。 在此过程中，用于着色的扫描程序还用于确定令牌和令牌是否可以触发匹配大括号操作的类型。 如果找到该触发器，则<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>调用方法来查找匹配的大括号。 最后，将突出显示两个大括号。  
  
 即使大括号的触发器的名称中使用，并分析原因，此过程并不局限于实际的大括号。 支持的字符指定要匹配的对任何对。 示例包括 （和）\<和 >，和 [和]。  
  
 假定该语言服务支持匹配的大括号。  
  
1.  用户键入右大括号 （}）。  
  
2.  源文件中光标位置处插入的大括号，光标高级 1。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>中的方法<xref:Microsoft.VisualStudio.Package.Source>类调用使用类型化的右大括号。  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法调用<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>中的方法<xref:Microsoft.VisualStudio.Package.Source>类来获取当前光标位置前的位置处的令牌。 此令牌对应于类型化的右大括号）。  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法调用<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法<xref:Microsoft.VisualStudio.Package.Colorizer>对象以获取在当前行的所有令牌。  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法调用<xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>方法<xref:Microsoft.VisualStudio.Package.IScanner>对象与当前行的文本。  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法重复调用<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>方法<xref:Microsoft.VisualStudio.Package.IScanner>对象从当前行中收集所有令牌。  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法调用的私有方法<xref:Microsoft.VisualStudio.Package.Source>类来获取令牌，其中包含所需的位置，并从获取传入的令牌的列表<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法。  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法查找的一个令牌触发器标志<xref:Microsoft.VisualStudio.Package.TokenTriggers>从返回的令牌上<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法; 即，表示右大括号的令牌)。  
  
6.  如果触发器标志的<xref:Microsoft.VisualStudio.Package.TokenTriggers>找到，则<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>中的方法<xref:Microsoft.VisualStudio.Package.Source>类名。  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>方法将分析操作开头的分析原因值<xref:Microsoft.VisualStudio.Package.ParseReason>。 此操作最终调用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>类。 如果启用了异步分析，则此调用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法发生在后台线程上。  
  
8.  在分析操作完成时，名为内部完成处理程序 （也称为回调方法）`HandleMatchBracesResponse`中称为<xref:Microsoft.VisualStudio.Package.Source>类。 会自动进行此调用<xref:Microsoft.VisualStudio.Package.LanguageService>基类，不是由分析器。  
  
9. `HandleMatchBracesResponse`方法获取从范围列表<xref:Microsoft.VisualStudio.Package.AuthoringSink>对象存储在<xref:Microsoft.VisualStudio.Package.ParseRequest>对象。 (跨度<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>结构，它在源文件中指定的一系列行和字符。)此列表的范围通常包含两个范围，每个用于括号和右大括号。  
  
10. `HandleBracesResponse`方法调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>对象存储在<xref:Microsoft.VisualStudio.Package.ParseRequest>对象。 这样可以突出显示的给定的范围。  
  
11. 如果<xref:Microsoft.VisualStudio.Package.LanguagePreferences>属性<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>启用，则`HandleBracesResponse`方法获取包含匹配的范围，并在状态栏中显示范围的第一次 80 个字符的文本。 这最适用如果<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法包含附带匹配的对的语言元素。 有关更多信息，请参见 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 属性。  
  
12. 完成操作。  
  
### <a name="summary"></a>摘要  
 通常局限于的语言元素的简单对匹配的大括号操作。 更复杂的元素，如匹配三元组 ("`if(...)`"，"`{`"和"`}`"，或"`else`"，"`{`"和"`}`")，可以突出显示为单词完成操作的一部分。 例如，完成"else"word 时，相匹配的"`if`"语句可以突出显示。 如果没有一系列`if` / `else if`语句，所有这些无法通过使用相同的机制，作为匹配的大括号突出显示。 <xref:Microsoft.VisualStudio.Package.Source>基类已支持此操作，请按如下所述： 扫描仪必须返回令牌触发器值<xref:Microsoft.VisualStudio.Package.TokenTriggers>与触发器值结合使用<xref:Microsoft.VisualStudio.Package.TokenTriggers>为的光标位置之前的令牌。  
  
 有关详细信息，请参阅[旧语言服务中的大括号匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)。  
  
## <a name="parsing-for-colorization"></a>分析着色  
 着色源代码非常简单，只需确定的有关该类型的令牌和返回颜色信息的类型。 <xref:Microsoft.VisualStudio.Package.Colorizer>类充当编辑器和扫描程序，提供有关每个令牌的颜色信息之间的媒介。 <xref:Microsoft.VisualStudio.Package.Colorizer>类使用<xref:Microsoft.VisualStudio.Package.IScanner>帮助着色行以及还收集源文件中的所有行的状态信息的对象。 在 MPF 语言服务类中，<xref:Microsoft.VisualStudio.Package.Colorizer>类没有需要重写，因为它与扫描程序只能通过<xref:Microsoft.VisualStudio.Package.IScanner>接口。 提供实现的对象<xref:Microsoft.VisualStudio.Package.IScanner>接口通过重写<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>类。  
  
 <xref:Microsoft.VisualStudio.Package.IScanner>扫描程序有源代码通过一套<xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>方法。 调用<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>方法重复以获取行中的下一个标记，直到行耗尽的令牌。 有关着色、 MPF 视为行组成的序列中添加所有源代码。 因此，扫描程序必须能够应对与作为行即将在它的源。 此外，任何行可以在任何时候，传递到扫描程序，并且只能保证是扫描程序从前要扫描的行的一行接收状态变量。  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer>类还用于确定令牌的触发器。 这些触发器告诉 MPF 特定令牌可以启动一个更复杂的操作，如 word 完成或匹配的大括号。 标识此类触发器必须快速，并且必须出现在任何位置，因为扫描程序是最适合此任务。  
  
 有关详细信息，请参阅[旧语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。  
  
## <a name="parsing-for-functionality-and-scope"></a>分析功能和作用域  
 分析功能和作用域需要比只标识遇到的令牌的类型的更多工作。 分析器必须标识不仅令牌类型，而且还对其使用该令牌的功能。 例如，标识符是只是名称，但在你的语言，标识符可能是类、 命名空间、 方法或变量，具体取决于上下文的名称。 令牌的常规类型可能是标识符，但标识符也可能具有其他含义，具体取决于它是什么和定义它。 此标识需要分析器具有更广泛的知识有关正在分析的语言。 这就是<xref:Microsoft.VisualStudio.Package.AuthoringSink>进入时类。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>类收集有关标识符、 方法、 匹配的语言对 （如大括号和括号），和语言三元组的信息 (类似于语言对不同的是三个部分，例如，"`foreach()`""`{`"和"`}`")。 此外，你可以重写<xref:Microsoft.VisualStudio.Package.AuthoringSink>类，以支持使用在早期验证断点，以便调试器不一定要加载，代码标识和**自动**调试窗口中，其中显示了本地变量和参数自动当程序正在调试并需要分析器来确定相应的本地变量和除调试器提供的参数。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink>对象作为的一部分传递到分析器<xref:Microsoft.VisualStudio.Package.ParseRequest>对象，并且新<xref:Microsoft.VisualStudio.Package.AuthoringSink>对象是每次创建一个新<xref:Microsoft.VisualStudio.Package.ParseRequest>创建对象。 此外，<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法必须返回<xref:Microsoft.VisualStudio.Package.AuthoringScope>对象，用于处理各种智能感知操作。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>对象维护声明的列表和列表的方法，或者其中填充，具体取决于分析的原因。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>必须实现类。  
  
## <a name="see-also"></a>另请参阅  
 [实现旧语言服务](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [旧语言服务概述](../../extensibility/internals/legacy-language-service-overview.md)   
 [在旧语言服务中的语法着色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [旧版语言服务中的大括号匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)