---
title: "要开始使用 Visual Studio 中的调试器 |Microsoft 文档"
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 0b3138c4-b840-446a-a15c-10ed8e2dd050
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68eb471f1db42b60114c2a14745ba4771b640c0d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="get-started-with-the-visual-studio-debugger"></a>要开始使用 Visual Studio 调试器
Visual Studio 调试器在任何语言环境下都易于使用。 下面我们将介绍如何调试一个简单的 C# 程序，但你可以对 c + + 和 JavaScript 等其他语言中的代码应用相同的步骤。

若要观看视频显示类似的功能，请参阅[调试器入门](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6)。
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a>调试一个基本 C# 项目  
 让我们从简单的 C# 控制台应用开始 (**文件 > 新建 > 项目**，然后选择**Visual C#**然后**控制台应用程序**)。 如果你从未使用 Visual Studio 之前过，请参阅[演练： 创建简单的应用程序](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)。 **Main**方法只需将 1 添加到一个整数变量 10 次，并打印到控制台的结果：  
  
```CSharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 生成此代码**调试**配置。 默认情况下已设置此配置。 有关配置的详细信息，请参阅[了解生成配置](../ide/understanding-build-configurations.md)。  
  
 在调试器中运行此代码，通过单击**调试 > 启动调试**(或**启动**的工具栏上，或**F5**)。 应用程序应几乎立即退出，因此实际上无法判断是否打印了任何内容在控制台窗口。  
  
 你可以停止执行足够长的时间以查看“控制台”窗口，方法是设置一个断点然后单步前进。 若要设置断点，请将光标放`Console.WriteLine`行，然后单击**调试 > 新断点 > 函数断点**，或只需单击同一行的左边距中。 断点应如下所示：  
  
 ![设置断点](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 有关断点的详细信息，请参阅[使用断点](../debugger/using-breakpoints.md)。  
  
##  <a name="BKMK_Inspect_Variables"></a>检查变量  
 调试通常涉及到查找不包含所需值的特定点的变量。 我们将演示一些你可以检查变量的方法。  
  
 再次开始调试。 在执行 `Console.WriteLine` 代码之前停止执行。 你可以使其执行通过单步前进 (单击**调试 > 逐过程**或**F10**)。 在这种情况下你可能已选择**单步执行**(**F11**) 并获得了相同的结果; 我们稍后将介绍差异。 具有方法的最后一个大括号的行应已变为黄色。 查看控制台窗口。 你应该会看到**10**。  
  
 你可以将鼠标悬停在**局部变量**变量以在数据提示中查看的当前值。  
  
 ![DBG &#95;基础知识 &#95; 数据 &#95;提示](../debugger/media/dbg_basics_data_tips.png "DBG_Basics_Data_Tips")  
  
 紧靠代码窗口正下方，你应看到**自动**，**局部变量**，和**监视**windows。 在执行时，这些窗口将显示变量的当前值。 这两个**自动**和**局部变量**windows 显示**局部变量**值为**10**。  
  
 ![自动窗口在调试时](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 有关这些时窗口的详细信息，请参阅[自动和局部变量窗口](../debugger/autos-and-locals-windows.md)。  
  
 让我们看看我们逐步完成程序变量的值的更改方式。 上设置断点`testInt += 1;`行，然后重新启动调试。 您应该会看到**局部变量**中**局部变量**和**自动**窗口是**0**，和**我**是**1**。 当你继续调试 (**调试 > 继续**，或**继续**的工具栏上，或**F5**)，你可以看到的值**局部变量**更改为**1**，然后**2**，依次类推。 当你厌倦了查看这些更改时，可删除断点 (**调试 > 切换断点**，或者在边距中单击)，然后继续调试。 如果你想要删除所有断点，请单击**调试 > 删除所有断点**，或**CTRL + SHIFT + F9**，然后单击**是**要求在对话框中**执行你想要删除所有断点？**.  
  
## <a name="stepping-into-and-over-function-calls"></a>单步执行和逐过程执行函数调用  
 你可以在调试器语句-by-语句中执行代码 (**单步执行**) 也可以执行代码，而调试器跳过函数 (**逐过程**) 可用于快速访问你更感兴趣 （的代码函数代码仍执行）。 你可以在同一调试会话中的这两种方法之间进行切换。  
  
 若要查看的区别**单步执行**和**逐过程**，我们需要添加由另一个方法调用的方法。 将方法添加到 C# 应用程序，并从 Main 方法中调用该方法。 代码应如下所示：  
  
```CSharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 在 Main 方法中的 `Method1();` 调用上设置断点并启动调试。 执行中断时，单击**调试 > 单步执行**(或**单步执行**的工具栏上，或**F11**)。 执行在 method1 () 中的第一个大括号处再次中断：  
  
 ![单步执行代码](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 停止调试并再次启动，然后当执行在断点处中断，则单击**调试 > 逐过程**(或**逐过程**的工具栏上，或**F10**)。 执行在 `Console.WriteLine("end");` 处再次中断。  
  
 如果你想要了解有关使用调试器浏览代码的详细信息，请参阅[使用调试器浏览代码](../debugger/navigating-through-code-with-the-debugger.md)。