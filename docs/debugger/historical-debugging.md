---
title: "历史调试 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 历史调试
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

历史调试是取决于 IntelliTrace 所收集的信息的模式模式。  它允许你向前和前后移动应用程序的执行，并检查其状态。  
  
 可以在 Visual Studio Enterprise 版（但不可在 Professional 或 Community 版）中使用 IntelliTrace。  
  
## 为什么要使用历史调试？  
 设置断点以查找 Bug 会是一件没有太多确定性的事情。  在紧邻代码中你怀疑可能存在 Bug 的位置设置断点，然后在调试中程序中运行应用程序，并希望命中断点且执行中断的位置可以揭示 Bug 的源。  如果没有命中，则需要尝试在代码中的其他位置设置断点并重新运行调试程序，反复执行测试步骤直到发现问题。  
  
 ![设置断点](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 可以使用 IntelliTrace 和历史调试在应用程序中四处漫游，并能在不设置断点、不重启调试且不重复测试步骤的情况下检查其状态（调用堆栈和局部变量）。  这可以为你节省大量时间，特别是在 Bug 位于需要很长时间才能完成执行的测试方案的深处时。  
  
## 如何开始使用历史调试？  
 默认启用 IntelliTrace。  只需决定你对哪些事件和函数调用感兴趣即可。  有关定义你想查看的内容的详细信息，请参阅 [IntelliTrace 功能](../debugger/intellitrace-features.md)。  有关使用 IntelliTrace 进行调试的逐步说明，请参阅[演练：使用 IntelliTrace](../debugger/walkthrough-using-intellitrace.md)。  
  
## 使用历史调试导航代码  
 让我们从有 Bug 的简单程序开始。  在 C\# 控制台应用程序中，添加以下代码：  
  
```c#  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 我们假设调用 `AddAll()` 后，`resultInt` 的预期值是 20（将 `testInt` 增量 20 次的结果）。  （我们还假设你无法看到 `AddInt()` 中的 Bug）但结果实际上是 44。  如何在不逐句通过 `AddAll()` 10 次的情况下找到 Bug？  可以使用历史调试更快速轻松地查找 Bug。  此处是具体说明：  
  
1.  在“工具”\/“选项”\/“IntelliTrace”\/“常规”中，确保启用了 IntelliTrace，然后选择 IntelliTrace 事件和调用信息选项。  如果没有选择此选项，则将无法看到导航线（如下所述）。  
  
2.  在 `Console.WriteLine(resultInt);` 行上设置断点。  
  
3.  开始调试。  代码执行到断点。  在**“局部变量”**窗口中，可以看到 `resultInt` 的值是 44。  
  
4.  打开**“诊断工具”**窗口（**“调试”\/“显示诊断工具”**）。  代码窗口应如下所示：  
  
     ![断点处的代码窗口](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  你应该在左边距旁边看到一个双箭头，就在断点上方。  此区域称为导航线，它用于历史调试。  单击箭头。  
  
     在代码窗口中，应该看待前面的代码行 \(`int resultInt = AddIterative(testInt);`\) 变为粉红色。  在窗口上方，应该看到一条消息，告知你现在处于历史调试模式中。  
  
     代码窗口现在如下所示：  
  
     ![历史调试模式下的代码窗口](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  现在，可以单步执行 `AddAll()` 方法（使用**“F11”**键，或导航线中的**“单步执行”**按钮）。  单步前进（使用**“F10”**键，或导航线中的**“转到下一个调用”**）。  粉红色的行现在变为 `j = AddInt(j);` 行。  在这种情况下，**“F10”**键不会单步执行到下一行代码。  相反，它将单步执行到下一个函数调用。  历史调试在调用之间进行导航，并跳过不包括函数调用的代码行。  
  
7.  现在单步执行到 `AddInt()` 方法。  应该立即看到此代码中的 Bug。  
  
 此过程仅粗略介绍使用历史调试可以完成的事项。  要了解有关不同设置和导航线中不同按钮的效果的详细信息，请参阅 [IntelliTrace 功能](../debugger/intellitrace-features.md)。