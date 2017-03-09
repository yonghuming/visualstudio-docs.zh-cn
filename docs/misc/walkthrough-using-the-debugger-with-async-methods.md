---
title: "演练：将调试器与异步方法一起使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "异步功能, 使用调试器"
  - "await 运算符, 使用调试器"
  - "“逐语句”命令, 在 await 运算符处"
  - "“跳出”命令, 在异步方法中"
  - "“逐过程”命令, 在 await 运算符处"
ms.assetid: 5adb2531-3f09-4b7e-8baa-29de80abee6e
caps.latest.revision: 23
caps.handback.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# 演练：将调试器与异步方法一起使用
通过使用异步功能，您可以调用异步方法而无需使用回调，也不需要跨多个方法或 lambda 表达式来拆分代码。  若要使同步代码异步，请调用异步方法而非同步方法，并向代码中添加几个关键字。  有关详细信息，请参阅[使用 Async 和 Await 的异步编程](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 在 Visual Studio 调试器中，您可将**“单步执行”**、**“逐过程”**和**“跳出”**命令与 `Async` 功能结合使用。  还可继续使用断点，特别是查看包含 await 运算符的语句处的控制流。  在本演练中，您将完成下列任务，可按任意顺序运行这些任务。  
  
-   使用断点演示 await 语句处的控制流。  
  
-   了解**“单步执行”**和**“逐过程”**命令在包含 await 运算符的语句处的行为。  
  
-   了解从异步方法使用**“跳出”**命令时，该命令的行为。  
  
## 用于显示控制流的断点  
 如果您使用 [Async](/dotnet/visual-basic/language-reference/modifiers/async) \(Visual Basic\) 或 [async](/dotnet/csharp/language-reference/keywords/async) \(C\#\) 修饰符标记方法，则可在方法中使用 [Await](/dotnet/visual-basic/language-reference/modifiers/async) \(Visual Basic\) 或 [await](/dotnet/csharp/language-reference/keywords/await) \(C\#\) 运算符。  若要创建 await 表达式，请将 operator 运算符与任务关联。  为任务调用 await 表达式时，当前方法将立即存在并返回不同的任务。  在与 await 运算符关联的任务完成时，在同一方法中继续执行。  有关详细信息，请参阅[异步程序中的控制流](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md)。  
  
> [!NOTE]
>  异步方法在遇到第一个尚未完成的 awaited 对象或到达异步方法的末尾（以先发生者为准）时将返回调用方。  
  
> [!NOTE]
>  这些示例中的控制台应用程序使用 <xref:System.Threading.Tasks.Task.Wait%2A> 方法阻止应用程序在 `Main` 中终止。  您不应在控制台应用程序之外使用 <xref:System.Threading.Tasks.Task.Wait%2A> 方法，因为这会出现死锁情况。  
  
 以下过程将断点设置演示应用程序到达 await 语句时发生的情况。  您还可通过添加 `Debug.WriteLine` 语句来演示控制流。  
  
1.  创建控制台应用程序，然后将以下代码粘贴到该应用程序中：  
  
     [!code-cs[csAsyncDebugging#1](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_1.cs)]
     [!code-vb[csAsyncDebugging#1](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_1.vb)]  
  
2.  在以“set breakpoint”注释结束的三个行上设置调试断点。  
  
3.  选择 F5 键，或选择菜单栏上的**“调试”**和**“启动调试”**来运行应用程序。  
  
     应用程序将进入 `ProcessAsync` 方法并在包含 await 运算符的行上中断。  
  
4.  再次选择 F5 键。  
  
     由于应用程序已在包含 await 运算符的语句上停止，因此应用程序将立即退出异步方法并返回一个任务。  因此，应用程序将退出 `ProcessAsync` 方法并在调用方法 \(`Main`\) 中的断点处中断。  
  
5.  再次选择 F5 键。  
  
     在 `DoSomethingAsync` 方法完成后，代码将在调用方法中的 await 语句后继续。  因此，应用程序将在 `ProcessAsync` 方法中的断点处中断。  
  
     在最初等待 `DoSomethingAsync` 后，`ProcessAsync` 方法将退出并返回一个任务。  之后，在等待的 `DoSomethingAsync` 方法完成后，计算 await 语句将生成 `DoSomethingAsync` 的返回值。  将定义 `DoSomethingAsync` 方法以在 Visual Basic 中返回 `Task (Of Integer)` 或在 C\# 中返回 `Task<int>`，因此其返回语句中的值为整数。  有关详细信息，请参阅 [异步返回类型](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md)。  
  
### 获取并等待任务  
 在 `ProcessAsync` 方法中，语句 `Dim result = Await DoSomethingAsync()` \(Visual Basic\) 或 `var result = await DoSomethingAsync();` \(C\#\) 是下列两个语句的缩写式：  
  
 [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
 [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
 第一行代码将调用异步方法并返回一个任务。  该任务将与下一行代码中的 await 运算符关联。  await 语句将退出方法 \(`ProcessAsync`\) 并返回一个不同的任务。  在与 await 运算符关联的任务完成后，代码将在 await 语句后的方法 \(`ProcessAsync`\) 中继续。  
  
 当 await 语句立即返回不同的任务时，该任务是包含 await 运算符的异步方法 \(`ProcessAsync`\) 的返回参数。  await 返回的任务包括出现在同一方法中的 await 之后的代码执行，这是此任务不同于与 await 关联的任务的原因。  
  
## 单步执行和逐过程  
 **“单步执行”**命令将单步执行方法，而**“逐过程”**命令将执行方法调用，然后在调用方法的下一行上中断。  有关详细信息，请参阅[单步执行、逐过程执行或跳出代码](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Step_into__over__or_out_of_the_code)。  
  
 以下过程演示当您在 await 语句处选择**“单步执行”**或**“逐过程”**命令后将发生的情况。  
  
1.  将控制台应用程序中的代码替换为以下代码。  
  
     [!code-cs[csAsyncDebugging#3](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_3.cs)]
     [!code-vb[csAsyncDebugging#3](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_3.vb)]  
  
2.  选择 F11 键，或选择菜单栏上的**“调试”**和**“单步执行”**，以在包含 await 运算符的语句处开始演示 `Step Into` 命令。  
  
     应用程序将启动并在第一行（在 Visual Basic 中为 `Sub Main()` 或在 C\# 中为 `Main` 方法的左大括号）上中断。  
  
3.  再选择 F11 键三次。  
  
     应用程序现在应位于 `ProcessAsync` 方法中的 await 语句处。  
  
4.  选择 F11 键。  
  
     应用程序将进入 `DoSomethingAsync` 方法并在第一行上中断。  即使应用程序将立即返回到 `await` 语句处的调用方法 \(`Main`\)，此行为也将出现。  
  
5.  一直选择 F11 键，直至应用程序返回到 `ProcessAsync` 方法中的 await 语句。  
  
6.  选择 F11 键。  
  
     应用程序将在 await 语句后面的行上中断。  
  
7.  在菜单栏上，选择**“调试”**和**“停止调试”**来停止执行应用程序。  
  
     后续步骤演示 await 语句处的**“逐过程”**命令。  
  
8.  选择 F11 键四次，或选择菜单栏上的**“调试”**和**“单步执行”**四次。  
  
     应用程序现在应位于 `ProcessAsync` 方法中的 await 语句处。  
  
9. 选择 F10 键，或选择菜单栏上的**“调试”**和**“逐过程”**。  
  
     执行将在 await 语句后面的行上中断。  即使应用程序立即返回到 await 语句处的调用方法 \(`Main`\)，此行为也将出现。  `Step Over` 命令还将按预期跳出 `DoSomethingAsync` 方法的执行。  
  
10. 在菜单栏上，选择**“调试”**和**“停止调试”**来停止执行应用程序。  
  
     如下列步骤所示，当 await 运算符位于与对异步方法的调用不同的行上时，**“单步执行”**和**“逐过程”**命令的行为会略有不同。  
  
11. 在 `ProcessAsync` 方法中，将 await 语句替换为以下代码。  原始 await 语句是下面两个语句的缩写式。  
  
     [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
     [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
12. 选择 F11 键或选择菜单栏上的**“调试”**和**“单步执行”**多次，以开始执行并单步执行代码。  
  
     在对 `DoSomethingAsync` 的调用中，**“单步执行”**命令在 `DoSomethingAsync` 方法中中断，而**“逐过程”**命令按预期进入下一语句。  在 await 语句中，这两种命令都在 await 后面的语句处中断。  
  
## 跳出  
 在非异步方法中，**“跳出”**命令将在方法调用后面的代码上的调用方法中中断。  对于异步方法，其中执行将在调用方法中中断的逻辑更复杂，此逻辑取决于**“跳出”**命令是否位于异步方法的第一行。  
  
1.  将控制台应用程序中的代码替换为以下代码。  
  
     [!code-cs[csAsyncDebugging#4](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_4.cs)]
     [!code-vb[csAsyncDebugging#4](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_4.vb)]  
  
2.  在 `DoSomethingAsync` 方法中的 `Debug.WriteLine("before")` 行上设置断点。  
  
     这是为了从不是异步方法中的第一行的某个行中演示**“跳出”**命令的行为。  
  
3.  选择 F5 键，或选择菜单栏上的**“调试”**和**“启动调试”**来启动应用程序。  
  
     代码将在 `DoSomethingAsync` 方法中的 `Debug.WriteLine("before")` 上中断。  
  
4.  选择 Shift\+F11 键，或选择菜单栏上的**“调试”**和**“跳出”**。  
  
     应用程序将在与当前方法关联的任务的 await 语句处的调用方法中中断。  因此，应用程序将在 `ProcessAsync` 方法中的 await 语句上中断。  应用程序不会在 `Dim z = 0` \(Visual Basic\) 或 `int z = 0;` \(C\#\) 上中断，它是对 `DoSomethingAsync` 方法的调用后面的代码。  
  
5.  选择菜单栏上的**“调试”**和**“停止调试”**来停止执行应用程序。  
  
     后续步骤演示在从异步方法的第一行**“跳出”**时将发生的情况。  
  
6.  移除现有断点，并在 `DoSomethingAsync` 方法的第一行上添加断点。  
  
     在 C\# 中，在 `DoSomethingAsync` 方法的左大括号处添加断点。  在 Visual Basic 中，在包含 `Async Function DoSomethingAsync() As Task(Of Integer)` 的行上添加断点。  
  
7.  选择 F5 键以启动应用程序。  
  
     代码将在 `DoSomethingAsync` 方法的第一行上中断。  
  
8.  在菜单栏上，依次选择**“调试”**、**“窗口”**和**“输出”**。  
  
     将打开**“输出”**窗口。  
  
9. 选择 Shift\+F11 键，或选择菜单栏上的**“调试”**和**“跳出”**。  
  
     应用程序将继续执行，直到异步方法到达其第一个 await，然后应用程序将在调用语句处中断。  因此，应用程序将在 `Dim the Task = DoSomethingAsync()` \(Visual Basic\) 或 `var theTask = DoSomethingAsync();` \(C\#\) 上中断。  “before”消息已显示在“输出”窗口中，而“after”消息尚未显示。  
  
10. 选择 F5 键以继续运行应用程序。  
  
     应用程序将继续执行已调用的异步函数 \(`DoSomethingAsync`\) 中的 await 语句后面的语句。  “after”消息将显示在“输出”窗口中。  
  
## 请参阅  
 [使用调试器浏览代码](../debugger/navigating-through-code-with-the-debugger.md)