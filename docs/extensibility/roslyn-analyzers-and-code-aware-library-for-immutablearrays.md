---
title: "Roslyn 分析器和代码识别库 ImmutableArrays |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b33516bd013f744813b2fdb357f224bcb0d9822
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Roslyn 分析器和代码识别 ImmutableArrays 库

[.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") 可帮助你生成代码识别的库。  代码识别的库提供了你可以使用的功能和工具 （Roslyn 分析器） 来帮助你使用的库中的最佳方法，或若要避免错误。  本主题演示如何生成以捕获常见错误使用时的实际 Roslyn 分析器[System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) NuGet 包。  该示例还演示如何为分析器发现的代码问题提供的代码修复。  用户请参阅在 Visual Studio 电灯泡 UI 的代码修复，并且可以自动将应用的代码修复。

## <a name="getting-started"></a>入门

需要下列项才能生成此示例：

* Visual Studio 2015 (非 Express Edition) 或更高版本。  你可以使用免费[Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  你也可以在安装 Visual Studio 中，检查在常用的工具在同一时间安装 SDK 的 Visual Studio 扩展性工具。  如果你已安装 Visual Studio，则还可以通过转到主菜单来安装此 SDK**文件 &#124;新 &#124;项目...**，在左侧的导航窗格中，选择 C#，然后选择扩展性。  当你选择"**安装 Visual Studio 扩展性工具**"痕迹导航项目模板，它将提示你下载并安装 SDK。
* [.NET compiler Platform ("Roslyn") SDK](http://aka.ms/roslynsdktemplates)。  你还可以通过转到主菜单上安装此 SDK**文件 &#124;新 &#124;项目...**，选择**C#**在左侧的导航窗格中，并选择**扩展性**。  当你选择"**下载.NET 编译器平台 SDK**"痕迹导航项目模板，它将提示你下载并安装 SDK。  此 SDK 包括[Roslyn 语法可视化工具](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)。  找出哪些代码模型类型此非常有用的工具可帮助你应该查找你分析器中。  到你的代码的特定代码模型类型，因此你的代码仅在必要时执行，并可以专注于分析相关的代码仅在分析器基础结构调用。

## <a name="whats-the-problem"></a>怎么了？

假设一个库提供 ImmutableArray (例如， <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) 支持。  C# 开发人员有很多与.NET 数组的经验。  但是，由于 ImmutableArrays 和优化方法的实现中使用的特性，C# 开发人员 intuitions 会导致你的库的用户编写中断的代码，如下所述。  此外，用户看不到运行时，不用于在 Visual Studio 中使用.NET 的质量体验到其错误。

用户熟悉编写代码如下所示：

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

创建空的数组进行填充后面的代码行和使用集合初始值设定项语法非常 C# 开发人员熟悉的。  但是，编写相同代码 ImmutableArray 崩溃在运行时：

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

第一个错误是由于 ImmutableArray 实现使用结构包装基础数据存储。 结构必须具有无参数构造函数，以便`default(T)`表达式可能返回所有结构零或 null 的成员。  当代码访问`b1.Length`，没有运行的时 null 取消引用错误，因为 ImmutableArray 结构中没有任何基础存储阵列。  创建空 ImmutableArray 的正确方法是`ImmutableArray<int>.Empty`。

因为 ImmutableArray.Add 方法将返回新的实例每次调用该函数，将发生该错误具有集合初始值设定项。  由于永远不会更改 ImmutableArrays，当你将添加一个新的元素，则将取回新 ImmutableArray 对象 （这可能会与先前存在 ImmutableArray 共享存储，出于性能原因）。  因为`b2`指向之前调用第一个 ImmutableArray`Add()`五次，`b2`的默认 ImmutableArray。  调用长度在其上还崩溃带 null 取消引用错误。  初始化 ImmutableArray 没有手动调用 Add 是使用的正确方法`ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`。

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>查找相关的语法来触发你分析器的节点类型

 若要开始生成分析器，首先计算出需要查找 SyntaxNode 哪种类型。 启动从菜单语法可视化工具**视图 &#124;其他 Windows &#124;Roslyn 语法可视化工具**。

编辑器的光标放置在声明行上`b1`。  你将看到语法可视化工具显示处于`LocalDeclarationStatement`的语法树的节点。  此节点具有`VariableDeclaration`，该子元素又具有`VariableDeclarator`，该子元素又具有`EqualsValueClause`，并且最后没有`ObjectCreationExpression`。  当单击节点的语法可视化工具树中时，在编辑器窗口中的语法突出显示，以显示该节点表示的代码。  SyntaxNode 子类型的名称匹配的 C# 语法中使用的名称。

## <a name="creating-the-analyzer-project"></a>创建分析器项目

在主菜单中选择**文件 &#124;新 &#124;项目...**.在**新项目**对话框下**C#**项目在左侧的导航栏中，选择扩展，然后在右窗格中选择**与代码修复分析器**项目模板。  输入一个名称，然后确认对话框。

模板将打开 DiagnosticAnalyzer.cs 文件。  选择该编辑器缓冲区选项卡。此文件具有分析器类 (格式为项目指定的名称)，派生自`DiagnosticAnalyzer`（Roslyn API 类型）。  你的新类`DiagnosticAnalyzerAttribute`声明你分析器是与 C# 语言，以便编译器发现并加载你分析器。

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

你可以实现使用以 C# 代码，为目标的 Visual Basic 分析器，反之亦然。  DiagnosticAnalyzerAttribute 选择你分析器指向一种语言，或者在更重要的是。  需要的语言的详细的建模的更复杂的分析器仅可具有一种语言。  如果你分析器中，例如，仅检查类型名称或公共成员名称，它可能可以使用跨 Visual Basic 和 C# Roslyn 提供通用语言模型。  例如，FxCop 会警告类将实现<xref:System.Runtime.Serialization.ISerializable>，但类不一定<xref:System.SerializableAttribute>特性是独立于语言的适用于 Visual Basic 和 C# 代码。

## <a name="initalizing-the-analyzer"></a>初始化词性分析器

 向下滚动有点`DiagnosticAnalyzer`类，以查看`Initialize`方法。  激活分析器时，编译器将调用此方法。  该方法采用`AnalysisContext`对象，它允许你分析器来获取上下文信息和注册回调的事件的种类的你想要分析的代码。

```csharp
public override void Initialize(AnalysisContext context) {}

```

打开一个新行方法和类型"在此上下文中。" 若要查看 IntelliSense 完成列表。  你可以看到完成列表中有许多`Register...`方法来处理各种类型的事件。  例如，第一个`RegisterCodeBlockAction`，返回到你的代码块，这通常是大括号之间的代码的调用。  注册一个块还调用返回到你的代码为初始值设定项的字段、 属性，所赋予的值或可选参数的值。

再举一例， `RegisterCompilationStartAction`，返回到你的代码开头的编译时，这很有用，当你需要通过多个位置中收集状态时调用。  你可以创建一种数据结构，即收集所有符号使用，并每次你分析器对于某些语法或符号，调用时返回可以将有关每个位置的信息保存在您的数据结构。  当你编译结束由于返回调用时，你可以分析你保存，例如，若要报告代码将使用从每个符号的所有位置`using`语句。

使用**语法可视化工具**，您学习了你想要当编译器处理 ObjectCreationExpression 时调用。  此代码用于设置回调：

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

你注册了语法节点和筛选器仅对象创建语法节点。  按照约定，分析器作者注册操作，这有助于保护分析器无状态时使用 lambda。  你可以使用 Visual Studio 功能**使用时生成**创建`AnalyzeObjectCreation`方法。  这太为你将生成正确的上下文参数类型。

## <a name="setting-properties-for-users-of-your-analyzer"></a>你分析器的用户设置属性

以便在你分析器在 Visual Studio 用户界面中相应地，查找并修改代码以标识你分析器的以下行：

```csharp
internal const string Category = "Naming";
```

Change `"Naming"` to `"API Guidance"`.

接下来查找和打开`Resources.resx`在你项目中使用的文件**解决方案资源管理器**。  你可以针对你的分析器、 标题等放入说明。你可以更改的值对于所有这些到`"Don't use ImmutableArray<T> constructor"`现在。  你可以将格式字符串 （{0}、 {1} 等） 中的自变量的字符串和更高版本在调用时`Diagnostic.Create()`，你可以提供`params`可传递的自变量的数组。

## <a name="analyzing-an-object-creation-expression"></a>分析对象创建表达式

`AnalyzeObjectCreation`方法采用不同类型的代码分析器框架通过提供上下文。  Initialize 方法`AnalysisContext`允许你注册操作回调，以设置你的分析器。  `SyntaxNodeAnalysisContext`，例如，具有`CancellationToken`，你可以传递。  如果用户启动时在编辑器中键入，Roslyn 将取消正在运行的分析器，以保存工作并提高性能。  再举一例，此上下文具有返回的对象创建语法节点的节点属性。

获取该节点，你可假定为其筛选语法节点操作的类型：

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>使用你分析程序第一次启动 Visual Studio

通过生成并执行你分析器启动 Visual Studio (按**F5**)。  由于启动项目中**解决方案资源管理器**是 VSIX 项目，你的代码和 VSIX 中，运行你的代码生成，并启动 Visual Studio 与安装该 VSIX。  以这种方式启动 Visual Studio，以便你的 Visual Studio 的主要用途将不会影响你的测试实例生成分析器时它将启动与不同的注册表配置单元中。  第一次启动这种方式，Visual Studio 进行类似于当你首次启动 Visual Studio 安装它后的几个初始化。

创建控制台项目，然后输入到控制台应用程序 Main 方法的数组代码：

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

使用代码的行`ImmutableArray`具有波形曲线，因为你需要获取不可变的 NuGet 包并添加`using`语句与你的代码。  中的项目节点按右指针按钮**解决方案资源管理器**选择**管理 NuGet 包...**.在 NuGet 管理器中，在搜索框中，键入"不可变"，然后选择项"System.Collections.Immutable"（不选择"Microsoft.Bcl.Immutable"） 中的左窗格中和按右窗格中的安装按钮。  安装包添加到项目引用的引用。

你仍看到下的红色波形曲线`ImmutableArray`，因此将光标放置在该标识符和按**CTRL +。** （句点） 以显示建议的修复方法菜单，然后选择添加相应`using`语句。

**全部保存并关闭**Visual Studio 现在将处于干净状态，以便继续第二个实例。

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>完成分析器使用编辑并继续

在 Visual Studio 的第一个实例，设置断点的开头你`AnalyzeObjectCreation`方法按**F9**的第一行上，插入符号。

启动重新与你分析器**F5**，并在 Visual Studio 的第二个实例中，重新打开控制台应用程序创建上一次。

因为 Roslyn 编译器看到的对象创建表达式，并且调用了你分析器，返回到 Visual Studio 的第一个实例，在断点处。

**获取对象创建节点。** 逐过程执行设置的行`objectCreation`变量按**F10**，然后在**即时窗口**计算表达式`"objectCreation.ToString()"`。  你看到变量指向的语法节点是代码`"new ImmutableArray<int>()"`，只查找的内容。

**获取 ImmutableArray < T\>类型对象。** 你需要检查是否正在创建的类型为 ImmutableArray。  首先，你将获取表示此类型的对象。  检查使用语义模型来确保你有完全正确的类型，并且您不将从 tostring （） 的字符串进行比较的类型。  输入以下函数末尾的代码行：

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

您指定中元数据与 backquotes （'） 和泛型参数数目的泛型类型。  正因如此，你看不到"...ImmutableArray\<T >"中的元数据名称。

语义模型在它让你提出有关符号、 数据流、 变量的生存期等问题上有许多有用的操作。Roslyn 从语义模型中分隔语法节点，由于各种工程原因 （性能，建模错误代码，等等）。  你想要查找有关准确比较的引用中包含的信息的编译模型。

您可以在编辑器窗口左侧拖动黄色执行指针。  将其拖到设置的行`objectCreation`变量和单步执行代码使用你新一行**F10**。  如果鼠标指针悬停在变量`immutableArrayOfType`，你会看到我们在语义模型中找到的确切类型。

**获取对象创建表达式的类型。** 用多种方式在本文中，使用"类型"，但这意味着如果你具有"新 Foo"表达式，您需要先获取 Foo 的模型。  你需要获取其类型的对象创建表达式，以查看它是否 ImmutableArray\<T > 类型。  再次使用语义模型对象创建表达式中获取类型符号 (ImmutableArray) 的符号信息。  输入以下函数末尾的代码行：

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

因为你 analyzer 需要处理编辑器缓冲区中的不完整或不正确的代码 (例如，没有缺少`using`语句)，则应检查`symbolInfo`正在`null`。  你需要获取已命名的类型 (INamedTypeSymbol) 从要完成分析的符号信息对象。

**比较类型。** 我们正在寻找，T 的开放式泛型类型，并且在代码中的类型是具体的泛型类型，因为查询从 （开放式泛型类型） 构造的类型的符号信息的虚拟机和模板，比较该结果与`immutableArrayOfTType`。  在输入以下命令方法末尾：

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**报告诊断。** 报告诊断是非常简单。  使用之前的 Initialize 方法定义的项目模板中为你创建的规则。  由于这种情况下在代码中时出现错误，您可以更改初始化规则要替换的行`DiagnosticSeverity.Warning`（绿色波形曲线） 与`DiagnosticSeverity.Error`（红色波形曲线）。  该规则的其余部分初始化从附近演练的开头部分编辑的资源。  你还需要报告波形曲线，表示对象创建表达式的类型规范的位置的位置。  输入此代码`if`块：

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

您的函数应如下所示 （可能是格式设置不同）：

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

删除断点，以便你可以查看让分析器运行 （并停止返回到 Visual Studio 的第一个实例）。  将执行指针拖动到的方法，并按开头**F5**以继续执行。  当你切换回 Visual Studio 的第二个实例时，编译器将启动以再次检查的代码，它将调入你分析器。  你可以看到在波浪线上`ImmutableType<int>`。

## <a name="adding-a-code-fix-for-the-code-issue"></a>添加代码问题的"代码修复"

在开始之前，关闭 Visual Studio 的第二个实例，并停止在 （其中你正在开发分析器） 的 Visual Studio 的第一个实例中进行调试。

**添加新类。** 在解决方案资源管理器中的项目节点上使用的快捷菜单 （右指针按钮） 并选择要添加新项。  添加一个名为类`BuildCodeFixProvider`。  此类必须派生自`CodeFixProvider`，并且你将需要使用**CTRL +。** （句点） 调用将添加正确的代码修复`using`语句。  此类还需要使用批注`ExportCodeFixProvider`特性，并且你将需要添加`using`语句以解决`LanguageNames`枚举。  你应具有与在它下面的代码的类文件：

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**存根派生成员。** 现在，编辑器的光标放置在标识符中`CodeFixProvider`按**CTRL +。** （句点） 以派生出抽象基类的实现。  这将为你生成一个属性和方法。

**实现的属性。** 填写`FixableDiagnosticIds`属性的`get`正文替换为以下代码：

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn 汇聚了诊断和修复的匹配这些标识符，都是字符串。  项目模板为你生成诊断 ID 和你可以自由地对其进行更改。  在属性中的代码只需从分析器类返回的 ID。

**RegisterCodeFixAsync 方法采用一个上下文。** 上下文非常重要，因为代码修复可以应用于多个诊断，或者的代码行上可能有多个问题。  如果你键入"上下文。" 在该方法的正文中，IntelliSense 完成列表将显示一些有用的成员。  没有可以检查以查看的内容是否想要取消此修补程序的 CancellationToken 成员。  没有文档成员具有大量有用的成员，并且使你能够获取对项目和解决方案模型对象。  范围成员开头，并且末尾的代码位置指定何时报告诊断。

**将此方法是异步的。** 你需要执行操作的第一件事是修复生成的方法声明为`async`方法。  针对出一个抽象类的实现按照存根的代码修复不包括`async`关键字，即使该方法返回`Task`。

**获取语法树的根。** 若要修改的代码需要生成新的语法树，但所做的更改你的代码修复使。  你需要`Document`要调用的上下文从`GetSyntaxRootAsync`。  这是异步方法，因为没有未知的工作用于获取语法树，可能包括从磁盘中获取该文件、 分析它，以及为其生成 Roslyn 代码模型。  在此期间，哪些使用 Visual Studio UI 应为响应`async`启用。  该方法中的代码行替换为以下代码：

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**查找有问题的节点。** 传入的上下文范围内，但您发现可能不是你需要更改代码的节点。  报告的诊断仅提供范围 （其中波形曲线所属） 的类型标识符，但你需要替换整个对象创建表达式，包括`new`开头和末尾括号的关键字。  将以下代码添加到你的方法 (并使用**CTRL +。** 若要添加`using`语句`ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**注册灯泡 UI 你代码修复。** 当你注册你的代码修复时，Roslyn 插入 Visual Studio 电灯泡 UI 自动。  最终用户将看到他们可以使用**CTRL +。** （句点），当你分析器的波形曲线错误`ImmutableArray<T>`构造函数使用。  由于你的代码修复提供程序仅执行时出现问题，你可以假定你具有您所查找的对象创建表达式。  通过上下文参数，你可以通过将下面的代码添加到末尾通过注册新的代码修复`RegisterCodeFixAsync`方法：

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

您需要将编辑器的插入符号放置在标识符， `CodeAction`，然后使用**CTRL +。** （句点） 添加相应`using`此类型的语句。

然后将放在编辑器的脱字号`ChangeToImmutableArrayEmpty`标识符和使用**CTRL +。** 再次，若要为您生成此方法存根。

添加此最后一个代码段通过传递注册的代码修复`CodeAction`和发现的问题的种类的诊断 ID。  在此示例中，没有只有一个此代码提供的诊断 ID 修补，以便您能够只需传递诊断的 Id 数组的第一个元素。  当你创建`CodeAction`，灯泡 UI 应使用的代码修复的说明作为文本中传递。  你还传递的函数中，采用 CancellationToken 并返回一个新文档。  新的文档具有新的语法树，它包括修补过，值调用的代码`ImmutableArray.Empty`。  此代码片段，以便它可以关闭通过 objectCreation 节点和上下文的文档使用 lambda。

**创建新的语法树。** 在`ChangeToImmutableArrayEmpty`方法更早版本，生成其存根 （stub） 输入的代码行： `ImmutableArray<int>.Empty;`。  如果再次查看该语法可视化工具工具窗口，你可以看到此语法是 SimpleMemberAccessExpression 节点。  这就是此方法需要以构造并返回新的文档中。

对第一个更改`ChangeToImmutableArrayEmpty`是添加`async`之前`Task<Document>`因为代码生成器无法采用该方法应是异步的。

填写的正文替换为以下代码，以便你的方法类似于以下：

```csharp
private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

你将需要置于编辑器的插入符号`SyntaxGenerator`标识符和使用**CTRL +。** （句点） 添加相应`using`此类型的语句。

此代码使用`SyntaxGenerator`，用于构造新代码是非常有用的类型。  获取文档的生成器具有代码问题后`ChangeToImmutableArrayEmpty`调用`MemberAccessExpression`、 传递具有我们想要访问的成员的类型和字符串形式传递成员的名称。

接下来，该方法会获取该文档的根和这可能涉及的一般情况下的任意工作，因为代码等待此调用，并将传递的取消标记。  Roslyn 代码模型是不可变，如使用.NET 字符串;当你更新字符串，可以新的字符串对象中返回。  当调用`ReplaceNode`，则将取回新的根节点。  大部分的语法树共享的 （因为它是不可变），但`objectCreation`节点替换`memberAccess`节点，以及到语法树的根的所有父节点。

## <a name="trying-your-code-fix"></a>尝试你的代码修复

现在，你可以按**F5**要在 Visual Studio 的第二个实例中执行你分析器。  打开之前使用的控制台项目。  现在你应会看到电灯泡显示新的对象创建表达式为`ImmutableArray<int>`。  如果按**CTRL +。** （期间），然后你会看到代码修复，并且您将看到电灯泡 UI 中自动生成的代码差异预览。  Roslyn 为你创建此操作。

**Pro 提示：**如果启动 Visual Studio 中，第二个实例并且未使用你的代码修复后，看到电灯泡，则可能需要清除 Visual Studio 组件缓存。  清除缓存强制 Visual Studio 以重新检查组件，以便 Visual Studio 应选取最新组件。  首先，关闭 Visual Studio 的第二个实例。  然后在 Windows 资源管理器，转到你的用户目录 (c:\users\\< userid\>) 并查找 AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\。  在此目录中删除的 ComponentModelCache 子目录。  "14"更改版本间使用 Visual Studio 中。

## <a name="talk-video-and-finish-code-project"></a>Talk 视频和完成代码项目

你可以看到开发并讨论了此示例中进一步[本次讨论](http://channel9.msdn.com/events/Build/2015/3-725)。  在不涉及演示工作分析器，并指导你完成生成它。

你可以看到所有完成的代码[此处](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)。  子文件夹 DoNotUseImmutableArrayCollectionInitializer 和 DoNotUseImmutableArrayCtor 每个已为查找问题和 C# 文件中实现的代码的修补程序显示在 Visual Studio 电灯泡 UI C# 文件。  请注意，完成的代码有少量的多个抽象，以免提取 ImmutableArray\<T > 反复类型对象。  它使用嵌套的已注册的操作将类型对象保存在可用的上下文中时的子操作 （分析对象创建和分析集合初始化） 执行。

## <a name="see-also"></a>另请参阅

* [\\\Build 2015 talk](http://channel9.msdn.com/events/Build/2015/3-725)
* [在 GitHub 上的已完成的代码](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [在 GitHub 上，几个示例分为三种类型的分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [GitHub OSS 站点上的其他文档](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [FxCop 规则实现与 GitHub 上的 Roslyn 分析器](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
