---
title: "Roslyn 分析器和代码感知 ImmutableArrays 库 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Roslyn 分析器和代码感知 ImmutableArrays 库
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[.NET 编译器平台](https://github.com/dotnet/roslyn) \("Roslyn"\) 可帮助您生成代码感知库。  代码感知库提供了可以使用的功能和工具 \(Roslyn 分析器\)，以帮助您使用的库以最佳方式，或若要避免错误。  本主题演示如何生成要在使用时捕获常见的错误的现实世界 Roslyn 分析器 [不可变的集合](../Topic/NIB:%20Immutable%20Collections.md) NuGet 程序包。  该示例还演示如何在分析器所找到的代码问题提供代码修补程序。  用户看到 Visual Studio 灯泡图标中用户界面中的代码修补程序，并可以自动应用针对代码的修复程序。  
  
## 主题内容  
 本主题包含以下各节:  
  
-   入门  
  
-   问题是什么?  
  
-   查找相关代码模型类型，以触发您的分析器  
  
-   创建分析器项目  
  
-   初始化在分析器  
  
-   为您的分析器的用户设置的属性  
  
-   分析对象创建表达式  
  
-   启动 Visual Studio 中使用您的分析器第一次  
  
-   完成分析器使用编辑并继续  
  
-   添加代码问题"的代码修复"  
  
-   尝试您的代码修补程序  
  
-   讨论视频的和已完成的代码项目  
  
## 入门  
 您需要以下内容以生成此示例中:  
  
-   Visual Studio 2015 \(非 Express Edition\) 或更高版本。  您可以使用免费 [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  您还可以在安装 Visual Studio 中，检查在常用的工具在同一时间安装该 SDK 的 Visual Studio 扩展性工具。  如果您已经安装了 Visual Studio，还可以通过转到主菜单安装此 SDK **文件 &#124;新 &#124;项目...**, ，在左侧的导航窗格中，选择 C\#，然后选择可扩展性。  当您选择"**安装 Visual Studio 扩展性工具**"痕迹导航项目模板，它会提示您先下载并安装 SDK。  
  
-   [.NET 编译器平台 \("Roslyn"\) SDK](http://aka.ms/roslynsdktemplates)。  您也可以安装此 SDK，请转到主菜单 **文件 &#124;新 &#124;项目...**, ，选择 **C\#** 在左侧的导航窗格中，并选择 **扩展性**。  当您选择"**下载.NET 编译器平台 SDK**"痕迹导航项目模板，它会提示您先下载并安装 SDK。  此 SDK 提供了 [Roslyn 语法可视化工具](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)。  找出哪些代码模型类型此极为有用的工具可帮助您应查找在您的分析器。  代码中存在特定的代码模型类型，因此您的代码仅执行在必要时，并可以仅重点分析相关的代码分析器基础结构调用。  
  
## 问题是什么?  
 假设您提供一个包含库 ImmutableArray \(例如， <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>\) 支持。  C\# 开发人员有很多与.NET 数组一起使用的经验。  但是，由于 ImmutableArrays 和优化方法的实现中使用的特性，C\# 开发人员 intuitions 导致您的库的用户能够在编写断开的代码，如下文所述。  此外，用户不会看到其错误直到运行时，这并不将其用于在 Visual Studio 中使用.NET 优质体验。  
  
 用户熟悉编写代码如下所示:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 创建空的数组，并在其中填入后面行和使用集合初始值设定项语法是代码的 C\# 开发人员对它很熟悉。  但是，编写相同在运行时崩溃 ImmutableArray 的代码:  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 第一个错误是由于 ImmutableArray 实施方案，使用一种结构来包装基础数据存储。  结构必须具有无参数构造函数，以便 `default(T)` 表达式可以返回所有结构零或 null 的成员。  当代码访问 `b1.Length`, ，没有运行的时 null 取消引用错误，因为没有基础的存储阵列没有 ImmutableArray 结构中。  若要创建空 ImmutableArray 的正确方式是 `ImmutableArray<int>.Empty`。  
  
 集合初始值设定项的错误是因为 ImmutableArray.Add 方法将返回新的实例每次调用该函数。  由于 ImmutableArrays 永远不会发生变化，当您添加新元素时，你将获取一个新的 ImmutableArray 对象 \(它可能会与先前存在 ImmutableArray 共享存储，出于性能原因\)。  因为 `b2` 指向之前调用第一个 ImmutableArray `Add()` 五次， `b2` 是默认值 ImmutableArray。  调用长度在其上还为 null 的崩溃取消引用错误。  若要使用手动调用 Add 是无需初始化 ImmutableArray 的正确方式 `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`。  
  
## 查找相关的语法节点类型，以触发您的分析器  
 若要开始构建在分析器，第一次计算出需要查找有关哪种类型的处理 SyntaxNode。    启动从菜单语法可视化工具 **视图 &#124;其他窗口 &#124;Roslyn 语法可视化工具**。  
  
 在声明行上放置编辑器的插入符号 `b1`。  您将看到语法可视化工具显示您处于 `LocalDeclarationStatement` 语法树的节点。  此节点有 `VariableDeclaration`, ，该子元素又具有 `VariableDeclarator`, ，该子元素又具有 `EqualsValueClause`, ，最后是 `ObjectCreationExpression`。  当您单击的语法可视化工具树中的节点，编辑器窗口中的语法突出显示以显示该节点表示的代码。  处理 SyntaxNode 子类型的名称匹配的 C\# 语法中使用的名称。  
  
## 创建分析器项目  
 从主菜单中选择 **文件 &#124;新 &#124;项目...**。  在 **新项目** 对话框下 **C\#** 项目在左侧的导航栏中，选择可扩展性，然后在右窗格中选择 **带有代码修补程序的分析器** 项目模板。  输入一个名称和确认对话框。  
  
 模板打开 diagnostic ­ Analyzer.cs 文件。  选择该编辑器缓冲区选项卡。  此文件具有一个分析器类 \(格式为项目指定的名称\) 派生的 `DiagnosticAnalyzer` \(Roslyn API 类型\)。  您的新类具有 `DiagnosticAnalyzerAttribute` 声明您的分析器是与 C\# 语言，以便编译器发现并加载您的分析器。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 您可以实现使用以 C\# 代码，为目标的 Visual Basic 的分析器，反之亦然。  很多重要 DiagnosticAnalyzerAttribute 选择您的分析器面向和 \/ 或一种语言中。  需要的语言的详细的建模的更复杂的分析器仅可具有一种语言。  如果您的分析器，例如，只检查类型名称或公共成员的名称，它可能可以使用 Roslyn 提供了跨 Visual Basic 和 C\# 中的公共语言模型。  例如，FxCop 会警告类将实现 <xref:System.Runtime.Serialization.ISerializable>, ，但该类不具有 <xref:System.SerializableAttribute> 特性是独立于语言的适用于 Visual Basic 和 C\# 代码。  
  
## 初始化词性分析器  
 向下滚动一点 `DiagnosticAnalyzer` 类以查看 `Initialize` 方法。  激活一个分析器时，编译器将调用此方法。  该方法采用 `AnalysisContext` 对象，它使您的分析器到达上下文信息以及如何注册回调的事件的类型的代码需要进行分析。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 打开一个新行方法和类型"在此上下文中。" 若要查看 Intellisense 完成列表。  您可以看到在完成列表中有很多 `Register…` 方法来处理各种类型的事件。  例如，第一个 `RegisterCodeBlockAction`, ，回调到您的代码块，这通常是大括号之间的代码。  注册一个块也回调到您的代码的字段、 提供给属性的值或可选参数的值的初始值设定项。  
  
 再举一例， `RegisterCompilationStartAction`, ，回调到您的代码在编译时，这很有用，当您需要通过多个位置收集状态的开头。  您可以创建一个数据结构，即收集所有符号使用，并每次您的分析器对于某些语法或符号后，调用时返回可以将有关每个位置的信息保存在您的数据结构。  您要在调用时返回由于编译结束，您可以分析已保存，例如，若要报告的代码使用从每个符号的所有位置 `using` 语句。  
  
 使用 **语法可视化工具**, ，您学习了您想要在编译器处理 ObjectCreationExpression 时调用。  此代码用于设置回调:  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 您注册了语法节点和仅对象创建语法节点的筛选器。  按照约定，分析器作者使用 lambda，注册帮助你使分析器无状态的操作时。  您可以使用 Visual Studio 功能 **根据使用情况生成** 创建 `AnalyzeObjectCreation` 方法。  这将生成正确的上下文参数类型为您太。  
  
## 为您的分析器的用户设置的属性  
 以便在您的分析器在 Visual Studio 用户界面中适当地，查找并修改代码以标识您的分析器的以下行:  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 更改 `"Naming"` 到 `"API Guidance"`。  
  
 接下来找到并打开 Resources.resx 文件在项目使用 **解决方案资源管理器**。  你可以为您的分析器、 标题等放置在描述中。可以为所有这些对象更改的值 `“Don’t use ImmutableArray<T> constructor”` 现在。  可以将格式字符串中的参数的字符串 \({0}，\\{1\\}，等等\)，及更高版本在调用时 `Diagnostic.Create()`, ，您可以提供要传递的参数的参数数组。  
  
## 分析对象创建表达式  
 `AnalyzeObjectCreation` 方法采用不同类型的代码分析器框架所提供的上下文。  Initialize 方法 `AnalysisContext` 允许您注册操作回调来设置您的分析器。`SyntaxNodeAnalysisContext`, ，例如，具有 `CancellationToken` ，您可以传递。  如果用户开始在编辑器中键入，Roslyn 将会取消正在运行分析器来保存工作并提高性能。  再举一例，此上下文中具有返回的对象创建语法节点的节点属性。  
  
 获取的节点，您可以假设是筛选出的语法节点操作的类型:  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
### 启动 Visual Studio 中使用您的分析器第一次  
 通过生成和执行您的分析器，启动 Visual Studio \(按 **F5**\)。  因为在启动项目中 **解决方案资源管理器** 是 VSIX 项目，您的代码和 VSIX，运行您的代码生成，并启动 Visual Studio 中使用该 VSIX 安装。  以这种方式启动 Visual Studio，以便您主要使用的 Visual Studio 将不会影响您的测试实例在构建分析器时它将启动具有独特的注册表配置单元中。  第一次启动这样一来，Visual Studio 进行类似于当您首次启动 Visual Studio 安装它之后的几个初始化操作。  
  
 创建一个控制台项目并数组代码然后进入您控制台应用程序的 Main 方法:  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 减少代码行数 `ImmutableArray` 具有波浪线，因为您需要获取不可变的 NuGet 程序包并添加 `using` 语句与您的代码。  中的项目节点上按右指针按钮 **解决方案资源管理器** ，然后选择 **管理 NuGet 包...**。  在 NuGet 管理器中，在搜索框中，键入"不可变"并选择项"System.Collections.Immutable"\(未选择"Microsoft.Bcl.Immutable"\) 中左窗格中按在右窗格中安装按钮。  安装包添加到你的项目引用的引用。  
  
 您将会看到下的红色波浪线 `ImmutableArray`, ，因此将光标放置在该标识符，然后按 **CTRL \+。** \(句点\)，以调出建议的修复方法菜单并选择将添加相应 `using` 语句。  
  
 **全部保存并关闭** 现在适用于 Visual Studio 将处于干净状态，以便继续第二个实例。  
  
## 完成分析器使用编辑并继续  
 在 Visual Studio 的第一个实例，在开始处设置断点您 `AnalyzeObjectCreation` 方法按 **F9** 的第一行上，插入符号。  
  
 启动您的分析器使用再次 **F5**, ，并在 Visual Studio 的第二个实例中，重新打开控制台应用程序创建最后一次。  
  
 因为 Roslyn 编译器看到对象创建表达式和名为您的分析器回到 Visual Studio 在断点处的第一个实例。  
  
 **获取对象创建节点。**跳过下面一行设置 `objectCreation` 变量按 **F10**, ，然后在 **即时窗口** 计算表达式 `“objectCreation.ToString()”`。  您看到的语法节点了变量指向是代码 `"new ImmutableArray<int>()"`, ，只您所寻找的内容。  
  
 **获取 ImmutableArray \< T \> 类型对象。**您需要检查是否正在创建的类型为 ImmutableArray。  首先，您将获取表示此类型的对象。  检查使用语义模型来确保完全正确的类型，并且不将从 tostring \(\) 的字符串进行比较的类型。  输入以下函数的末尾的代码行:  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 将指定元数据与 backquotes \('\) 和泛型参数数目中的泛型类型。  正因如此，您看不到"...ImmutableArray \< T \>"中的元数据名称。  
  
 语义模型具有许多有用的操作，您可以提出有关符号、 数据流、 变量生存期等问题。Roslyn 将与语义模型的语法节点分隔出于各种工程原因 \(性能，建模错误代码，等等\)。  您想要查找包含准确的比较的引用中的信息的编译模型。  
  
 您可以将黄色执行指针拖编辑器窗口的左侧。  将它设置行向上拖动 `objectCreation` 变量和逐过程执行您的代码使用新线 **F10**。  如果将鼠标指针悬停在变量 `immutableArrayOfType`, ，您看到我们在语义模型中找到的确切类型。  
  
 **获取对象创建表达式的类型。**在本文中，几种方法中使用"类型"但这意味着如果您具有"新 Foo"表达式中，您需要先获取 Foo 的模型。  您需要先获取对象创建表达式来确定是否 ImmutableArray \< T \> 类型的类型。  再次使用语义模型对象创建表达式中获取类型符号 \(ImmutableArray\) 的符号信息。  输入以下函数的末尾的代码行:  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 因为您的分析器需要处理编辑器缓冲区中的不完整或不正确的代码 \(例如，没有缺少 `using` 语句\)，则应检查 `symbolInfo` 正在 `null`。  您需要先获取命名的类型 \(INamedTypeSymbol\) 从符号信息对象来完成分析。  
  
 **比较类型。**因为我们正在寻找，T 的开放式泛型类型，并且代码中的类型是一个具体的泛型类型，您将查询从 \(开放式泛型类型\) 构造哪种类型的符号信息和比较该结果与 `immutableArrayOfTType`。  输入以下内容在该方法的末尾:  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 **报告诊断程序。**报告诊断是相当容易。  使用之前的初始化方法定义的项目模板中为您创建的规则。  由于这种情况下，在代码中的时出现错误，您可以更改初始化规则要替换的行 `DiagnosticSeverity.Warning` \(绿色的波浪线\) 与 `DiagnosticSeverity.Error` \(红色的波浪线\)。  该规则的其余部分初始化从本演练的开头附近编辑的资源。  您还需要报告波浪线，对象创建表达式的类型规范的位置的位置。  输入在此代码 `if` 块:  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 您的函数应如下所示 \(以不同的方式可能格式\):  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
 删除的断点，以便您可以查看分析器工作 \(并停止将返回到 Visual Studio 的第一个实例\)。  将执行指针拖动到的开头的方法，以及按 **F5** 以便继续执行。  当切换回 Visual Studio 的第二个实例时，编译器将启动以再次检查的代码，它将调用您的分析器。  您可以看到波浪线下的 `ImmutableType<int>`。  
  
## 添加代码问题"的代码修复"  
 在开始之前，关闭 Visual Studio 的第二个实例，并停止在 Visual Studio \(其中正在开发分析器\) 的第一个实例中进行调试。  
  
 **添加新类。**在您在解决方案资源管理器中的项目节点上使用的快捷菜单 \(右指针按钮\) 并选择要添加新项。  添加一个名为类 `BuildCodeFixProvider`。  此类必须派生自 `CodeFixProvider`, ，并将需要使用 **CTRL \+。** \(句点\) 来调用添加正确的代码修补程序 `using` 语句。  此类还需要使用批注 `ExportCodeFixProvider` 特性，并且您将需要添加 `using` 语句，以解决 `LanguageNames` 枚举。  您应该替换为以下代码在其中一个类文件:  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
 **存根 \(stub\) 出派生的成员。**现在，将编辑器的插入符号放在标识符中 `CodeFixProvider` ，然后按 **CTRL \+。** \(句点\) 彻底删除此抽象基类的实现。  这将为您生成的属性和方法。  
  
 **实现的属性。**填写 `FixableDiagnosticIds` 属性的 `get` 正文替换为以下代码:  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
 Roslyn 将结合在一起的诊断和修复的匹配这些都是字符串的标识符。  项目模板生成诊断 ID，并且你可以自由地将其更改。  在属性中的代码只需从分析器类返回的 ID。  
  
 **RegisterCodeFixAsync 方法采用一个上下文。**上下文很重要，因为代码修补程序，可以将应用于多个诊断程序，或在代码行上可能有多个问题。  如果键入"上下文中。 在该方法的正文中，Intellisense 完成列表将演示一些有用的成员。  没有一个 CancellationToken 成员，您可以查看的内容是否想要取消该修补程序。  没有具有许多有用的成员并使您可以向项目和解决方案模型对象的文档成员。  Span 成员开头，并且最终的代码位置指定何时报告诊断程序。  
  
 **请是异步的方法。**您需要执行的第一件事是解决生成的方法声明为 `async` 方法。  抽象类的实现将用作存根的代码修复并不包括 `async` 关键字，即使该方法返回 `Task`。  
  
 **获取语法树的根。**为修改的代码，您需要生成新的语法树所做的更改与您的代码修补程序进行。  您需要 `Document` 要调用的上下文从 `GetSyntaxRootAsync`。  这是异步方法，因为没有未知的工作来获取语法树中，还可能包括从磁盘中获取该文件，分析它，和为其生成 Roslyn 代码模型。  Visual Studio UI 应在此期间，哪些使用响应式 `async` 启用。  该方法中的代码行替换以下内容:  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
 **查找与问题的节点。**您传入的上下文范围内，但您发现可能不是您需要更改的代码的节点。  报告的诊断的范围仅用于 \(其中波形曲线上所属\) 的类型标识符，但您需要替换整个对象创建表达式，其中包括 `new` keywoard 在开头和结尾的括号。  将以下代码添加到您的方法 \(并使用 **CTRL \+。** 添加 `using` 语句 `ObjectCreationExpressionSyntax`\):  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
 **注册灯泡图标中 UI 您代码修补程序。**注册您的代码修补程序时，Roslyn 已插入到 Visual Studio 灯泡图标中 UI 自动。  最终用户将看到他们可以使用 **CTRL \+。** \(句点\)，当您的分析器的波形曲线错误 `ImmutableArray<T>` 构造函数使用。  因为代码修复提供程序只会出现问题时执行，可以假定您有您要查找的对象创建表达式。  从上下文参数，您可以通过下面的代码添加到末尾的注册新的代码修补程序 `RegisterCodeFixAsync` 方法:  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
 您需要将编辑器的插入符号放在标识符， `CodeAction`, ，然后使用 **CTRL \+。** \(句点\)，以添加适当 `using` 这种类型的语句。  
  
 然后将放在编辑器的脱字号 `ChangeToImmutableArrayEmpty` 标识符和使用 **CTRL \+。** 再次来为您生成此方法存根 \(stub\)。  
  
 添加此最后一个代码段注册代码修补程序，通过传递 `CodeAction` 和诊断发现问题的类型 ID。  在此示例中，没有只有一个此代码提供的诊断 ID 修复程序，以便您能够只需传递诊断的 Id 数组的第一个元素。  当您创建 `CodeAction`, ，您传入灯泡图标中 UI 应使用的代码修补程序的说明的文本。  你还传递的函数中采用 CancellationToken 并返回一个新的文档。  新的文档具有新的语法树，它包括已应用修补程序的代码中调用 `ImmutableArray.Empty`。  此代码段，以便它可以关闭 over objectCreation 节点和上下文的文档使用 lambda。  
  
 **创建新的语法树。**在 `ChangeToImmutableArrayEmpty` 方法更早版本，生成的存根中输入的代码行: `ImmutableArray<int>.Empty;`。  如果您再次查看语法可视化工具工具窗口，可以看到这种语法是即 simplememberaccess ­ Expression 节点。  这就是此方法需要以构造并返回一个新的文档。  
  
 对第一个更改 `ChangeToImmutableArrayEmpty` 是添加 `async` 之前 `Task<Document>` 因为代码生成器不能假定该方法应该是异步。  
  
 填写正文替换为以下代码，以便您的方法看起来类似以下所示:  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
 您需要将编辑器的插入符号放入 `SyntaxGenerator` 标识符和使用 **CTRL \+。** \(句点\)，以添加适当 `using` 这种类型的语句。  
  
 此代码使用 `SyntaxGenerator`, ，用于构造新的代码是非常有用的类型。  获取文档的生成器具有代码问题后 `ChangeToImmutableArrayEmpty` 调用 `MemberAccessExpression`, 、 传递具有我们想要访问的成员的类型和字符串形式传递的成员名称。  
  
 接下来，方法提取该文档的根，因为这可能会涉及的一般情况下的任意工作，该代码等待此调用，并将传递的取消标记。  Roslyn 代码模型是固定不变，象处理一个.NET 字符串;更新字符串时，将获得一个新字符串对象中返回。  当您调用 `ReplaceNode`, ，得到一个新的根节点。  大部分的语法树共享的 \(因为它是不可变\)，但 `objectCreation` 节点替换为 `memberAccess` 节点，以及最多的语法树的根的所有父节点。  
  
## 尝试您的代码修补程序  
 现在，可以按 **F5** 要在 Visual Studio 的第二个实例中执行您的分析器。  打开使用以前使用的控制台项目。  现在，您应看到灯泡图标中显示新的对象创建表达式为 `ImmutableArray<int>`。  如果您按 **CTRL \+。** \(期间\)，则将会解决问题，您的代码，您将看到灯泡图标中用户界面中的自动生成的代码差异预览。  Roslyn 这将为您创建。  
  
 Pro 提示: 如果启动 Visual Studio 中，第二个实例，并且您看不到灯泡图标中与代码修补程序，则您可能需要清除 Visual Studio 组件缓存。  清除缓存将强制重新检查该组件，因此 Visual Studio 应选取最新组件的 Visual Studio。  首先，关闭 Visual Studio 的第二个实例。  然后在 Windows 资源管理器，转到您的用户目录 \(c:\\users\\ \< 用户 id \>\)，并查找 AppData\\Local\\Microsoft\\VisualStudio\\14.0Roslyn\\。  在此目录中删除的 ComponentModelCache 子目录。  "14"的更改版本间使用 Visual Studio 中。  
  
## 访谈视频和完成的代码项目  
 您可以看到开发并讨论了此示例中进一步 [本次讨论](http://channel9.msdn.com/events/Build/2015/3-725)。  此次对话演示工作分析器，并指导您生成它。  
  
 您可以看到所有完成的代码 [此处](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)。  子文件夹 DoNotUseImmutableArrayCollectionInitializer 和 DoNotUseImmutableArrayCtor 每一个都有一个 C\# 文件用于查找问题和实现的代码修补程序，在 Visual Studio 灯泡图标中用户界面中显示一个 C\# 文件。  请注意，完成的代码有一些更多的抽象概念，可避免遍又一遍地提取 ImmutableArray \< T \> 类型对象。  它使用嵌套的已注册的操作将类型对象保存在可用的上下文中时的子操作 \(分析对象创建和分析集合初始化\) 执行。  
  
## 请参阅  
 [\\\\Build 2015年对话](http://channel9.msdn.com/events/Build/2015/3-725)   
 [在 github 上的已完成的代码](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)   
 [在 github 上，几个示例分为三种类型的分析工具](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)   
 [Github OSS 网站上的其他文档](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)   
 [通过在 github 上的 Roslyn 分析器实现的 FxCop 规则](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)