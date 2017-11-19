---
title: "导航代码与 Visual Studio 中的调试器 |Microsoft 文档"
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cda62de6fe72598674b90e4a0ef5dccd8cf2a2af
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="navigate-code-with-the-visual-studio-debugger"></a>导航代码通过 Visual Studio 调试器
熟悉的命令和快捷方式来浏览在调试器中的代码并将使变得更快、 更轻松地查找和解决你的应用程序中的问题。 虽然浏览在调试器中的代码，可以检查您的应用程序的状态或了解有关其执行流的详细信息。  
  
## <a name="start-debugging"></a>“启动调试”  
 通常情况下，启动调试会话使用**F5** (**调试** > **启动调试**)。 此命令启动附有调试器的应用程序。  
  
 绿色箭头还启动调试器 (与相同**F5**)。  
  
 ![DBG &#95;基础知识和 #95;开始 &#95; 调试](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")  
  
 你可以开始使用附有调试器的应用程序的几个其他方法包括**F11** ([单步执行代码](#BKMK_Step_into__over__or_out_of_the_code))， **F10** ([逐过程执行代码](#BKMK_Step_over_Step_out))，或通过使用**运行到光标处**。  在这些选项有什么作用，请参阅本主题面向信息的其他部分。  
  
 调试时，黄色线将显示下一步将执行的代码。  
  
 ![DBG &#95;基础知识和 #95;中断 &#95;模式](../debugger/media/dbg_basics_break_mode.png "DBG_Basics_Break_Mode")  
  
 调试时，你可以等命令之间进行切换**F5**， **F11**和使用其他功能，可用于快速访问你想要查看的代码 （例如断点） 的本主题中所述。  
  
 大多数调试器功能，例如，在局部变量窗口中查看变量值，或在监视窗口中计算表达式是可用的仅在暂停时调试器 (也称为*中断模式下*)。 调试器暂停时，你应用程序的状态已挂起函数，变量时，对象保留在内存中。 在中断模式下，你可以检查元素的位置和状态，以查看存在冲突或 bug。 对于某些项目类型，你还可以调整到在中断模式下应用。 若要观看视频显示这些功能，请参阅[调试器入门](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6)。
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a>单步执行代码逐行  
 若要在代码 （每个语句） 的每个行上停止调试时，使用**F11**键盘快捷方式 (或**调试** > **单步执行**菜单上)。  
  
> [!TIP]
>  执行的每一行代码时，你可以将鼠标悬停在变量以查看它们的值，或使用[局部变量](../debugger/autos-and-locals-windows.md)和[监视](../debugger/autos-and-locals-windows.md)窗口来监视更改其值。  
  
 以下是一些有关的行为的详细信息**单步执行**:  
  
-   在嵌套函数调用上， **“逐语句”** 将进入并单步执行嵌套最深的函数。 如果对类似 **的调用使用** “逐语句” `Func1(Func2())`，调试器将进入并单步执行函数 `Func2`。  
  
-   实际上，调试器逐句通过代码语句，而不是物理行。 例如， `if` 子句可以写在一行内：  
  
    ```CSharp  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```VB  
    Dim x As Integer = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     当你单步执行此行时，调试器将该条件视为一步，将结果视为另一步（在此示例中，条件为 true）。  
  
 若要直观地跟踪调用堆栈，单步执行函数时，请参阅[调试时映射调用堆栈上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
##  <a name="BKMK_Step_over_Step_out"></a>单步执行代码，跳过函数  
 当在调试器中运行代码，通常你会了解，你不需要查看特定的函数中会发生什么情况 (不关心或你知道工作，方式类似于经过的库代码)。 使用这些命令来跳过代码 （函数仍执行，当然，但调试器跳过它们）。  
  
|键盘命令|菜单命令|描述|  
|----------------------|------------------|-----------------|  
|**F10**|**逐过程**|如果当前行包含函数调用，**逐过程**运行的代码，然后在调用的函数返回之后在代码的第一行处挂起执行。|  
|**Shift + F11**|**跳出**|**单步跳出**会继续运行代码，在当前函数返回 （通过当前函数调试器跳） 时挂起执行。|  
  
> [!TIP]
>  如果你需要在你应用中查找的入口点，请先使用**F10**或**F11**。 检查你应用程序的状态或尝试了解有关其执行流的详细信息时，这些命令所通常很有用。  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>运行到特定位置或函数  
 通常调试代码的首选的方法，这些方法都很有用当你知道你想要检查，具体的代码时，或至少你知道你想要开始调试。  
  
-   **在代码中设置断点**  
  
     若要在代码中设置简单断点，请打开 Visual Studio 编辑器中的源文件。 设置光标的代码行中，你希望暂停执行、，然后右键单击代码窗口查看上下文菜单并选择**断点 > 插入断点**(或按**F9**)。 该代码行之前，调试器将暂停执行权限。  
  
     ![设置断点](../debugger/media/dbg_basics_setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Visual Studio 中的断点提供了一组丰富的附加功能，例如条件断点和跟踪点。 请参阅[使用断点](../debugger/using-breakpoints.md)。  
  
-   **运行到光标处**  
  
     若要运行到光标位置，请将光标放在源窗口中可执行的代码行上。 在编辑器的上下文菜单 （右键单击在编辑器中），选择**运行到光标处**。 这就像设置临时断点。

-   **运行到单击** 

    若要运行到在暂停时在调试器中在代码中的点，选择**到此处运行执行**绿色箭头图标 （你将看到悬停在某个代码行时图标）。 这消除了需要设置临时断点。

    ![调试器的运行到单击](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

    > [!NOTE]
    > **运行到单击**中的新增[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。
  
-   **手动中断代码**  
  
     若要在正在执行的应用程序上，中断下一个可用的代码行，请选择 **“调试”**、 **“全部中断”** （键盘： **Ctrl+Alt+Break**）。 
  
     如果中断正在执行的代码，而没有响应的源或符号 (.pdb) 文件，调试器将显示“未找到源文件”  或“未找到符号”  页面，帮助你找到相应的文件。 请参阅[指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。 如果你无法访问支持文件，仍可以在“反汇编”窗口中调试汇编指令。  
  
-   **在调用堆栈上运行到函数**  
  
     在**调用堆栈**窗口 （可在调试时），请选择的函数、 右键单击并选择**运行到光标处**。 若要直观地跟踪调用堆栈，请参阅[调试时映射调用堆栈上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
-   **运行到通过名称指定的函数**  
  
     你可以让调试器在运行你的应用程序，直至到达指定的函数。 你可以通过名称指定函数，也可以从调用堆栈中选择函数。  
  
     若要通过名称指定函数，请选择 **“调试”**、 **“新建断点”**、 **“在函数处中断”**，然后输入函数名称和其他标识信息。  
  
     ![新断点对话框](../debugger/media/dbg_execution_newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     如果是重载函数，或者函数在多个命名空间，你可以在 **“选择断点”** 对话框中选择想要的函数。  
  
     ![选择断点对话框](../debugger/media/dbg_execution_overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a>移动指针以更改执行流  
 在调试器暂停时，你可以移动指令指针，设置下一步要执行的代码语句。 源窗口或“反汇编”窗口的空白区域中的黄色箭头标记要执行的下一条语句的位置。 通过移动此箭头，可以跳过部分代码或返回到以前执行过的行。 在某些情况下可以使用此方法，例如，跳过包含已知 bug 的代码段。  
  
 ![将指针移](../debugger/media/dbg_basics_example3.gif "DBG_Basics_Example3")
  
 要设置下一条要执行的语句，请使用以下过程之一：  
  
-   在源窗口中，将黄色箭头拖动希望执行下一语句的位置，该位置应在同一源文件。  
  
-   在源窗口中，请将光标放置在你想要执行的下，右键单击并选择的行上**设置下一语句**。  
  
-   在反汇编窗口中，将光标放置在程序集指令，你想要执行下一步中，右键单击并选择**设置下一语句**。  
  
> [!CAUTION]
>  设置下一条语句将导致程序计数器直接跳到新位置。 使用此命令时要小心：  
>   
>  -   不执行旧执行点和新执行点之间的指令。  
> -   如果向后移动执行点，则不撤消插入的指令。  
> -   将下一条语句移动到另一个函数或范围通常会导致调用堆栈损坏，导致一个运行时错误或异常。 如果尝试将下一条语句移动到另一个范围，则调试器将打开一个含有警告的对话框，并提供一个取消该操作的机会。 在 Visual Basic 中，不能将下一条语句移动到另一个范围或函数。  
> -   在本机 C++ 中，如果已启用运行时检查，设置下一条语句会导致执行到达方法的结尾时引发异常。  
> -   当启用“编辑并继续”时，如果你进行了“编辑并继续”无法立即重新映射的编辑，那么 **“设置下一语句”** 将失败。 例如，如果你编辑了 catch 块中的代码，将发生这种情况。 在此情况下，你将看到错误消息，告诉你操作不受支持。  
  
> [!NOTE]
>  在托管代码中，在以下情况下不能移动下一条语句：  
>   
>  -   下一条语句与当前语句不在同一个方法中。  
> -   使用实时调试启动调试。  
> -   正在展开一个调用堆栈。  
> -   已引发一个 System.StackOverflowException 或 System.Threading.ThreadAbortException 异常。  
  
 应用程序处于活动运行状态时不能设置下一条语句。 要设置下一语句，调试器必须处于中断模式。  
  
## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>单步执行非用户代码  
 默认情况下，调试器尝试向你显示仅你应用代码调试时，该域由调试器名*仅我的代码*。 (请参阅[仅我的代码](../debugger/just-my-code.md)若要查看如何这适用于不同的项目类型和语言和如何您可以自定义行为。)但是，你在调试过程有时你可能想要查看框架代码，第三方库代码中或调用到操作系统 （系统调用）。  
  
 你可以关闭仅我的代码通过转到**工具** > **选项** > **调试**和清除**启用 '仅我的代码'**复选框。  
  
 当禁用仅我的代码时，调试器可以单步执行非用户代码和非用户代码显示在调试器窗口中。  
  
> [!NOTE]
>  设备项目不支持“仅我的代码”。  
  
 **单步执行系统调用**  
  
 如果你已加载系统代码的调试符号，且未启用仅我的代码，你可以单步执行系统调用中，就像其他任何调用。  
  
 若要访问 Microsoft 符号文件，请参阅[使用符号服务器查找不在本地计算机上的符号文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine)中[指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)主题。  
  
 在调试时加载特定系统组件的符号：  
  
1.  打开模块窗口 (键盘： **Ctrl + Alt + U**)。  
  
2.  选择要加载符号的模块。  
  
     查看 **“符号状态”** 列可以了解哪些模块加载了符号。  
  
3.  在上下文菜单中选择 **“加载符号”** 。  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 单步执行托管代码中的属性和运算符  
 默认情况下，调试器将逐过程执行托管代码中的属性和运算符。 在多数情况下，这会提供较好的调试体验。 若要启用单步执行属性或运算符，请选择**调试** > **选项**。 上**调试** > **常规**页上，清除**逐过程执行属性和运算符 （仅限托管）**复选框