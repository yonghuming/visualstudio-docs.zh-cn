---
title: "检查你的应用使用历史调试 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10d9e23912da2ee5d0af1b6d2f846fa1de2f94fe
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>检查 IntelliTrace 历史调试在 Visual Studio 中使用对应用程序
你可以使用[历史调试](../debugger/historical-debugging.md)向后移动和向前移动应用程序执行，以查看其状态。  
  
你可以在 Visual Studio Enterprise 版但不可在 Professional 或 Community 版中使用 IntelliTrace。  
  
## <a name="navigate-your-code-with-historical-debugging"></a>导航使用历史调试代码  
 让我们从有 bug 的简单程序开始。 在 C# 控制台应用程序中，添加以下代码：  
  
```CSharp  
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
  
 我们将假定的预期值`resultInt`之后调用`AddAll()`为 20 (的递增结果`testInt`20 倍)。 (我们还假设你无法看到中的 bug `AddInt()`)。但结果实际上是 44。 如何在不逐句通过 `AddAll()` 10 次的情况下找到 Bug？ 我们可以使用历史调试更快、 更轻松地查找 bug。 操作方法如下：  
  
1.  在**工具 > 选项 > IntelliTrace > 常规**，请确保启用了 IntelliTrace，然后选择**IntelliTrace 事件和调用信息**。 如果没有选择此选项，则将无法看到导航线（如下所述）。  
  
2.  在 `Console.WriteLine(resultInt);` 行上设置断点。  
  
3.  开始调试。 代码执行到断点。 在**局部变量**窗口中，你可以看到的值`resultInt`是 44。  
  
4.  打开**诊断工具**窗口 (**调试 > 显示诊断工具**)。 代码窗口应如下所示：  
  
     ![在断点处的代码窗口](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  你应该在左边距旁边看到一个双箭头，就在断点上方。 此区域称为导航线，用于历史调试。 单击箭头。  
  
     在代码窗口中，应该看待前面的代码行 (`int resultInt = AddIterative(testInt);`) 变为粉红色。 在窗口上方，你应看到一条消息，你现在处于历史调试。  
  
     代码窗口现在如下所示：  
  
     ![在历史调试模式下的代码窗口](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  现在可以单步执行`AddAll()`方法 (**F11**，或**单步执行**导航线中的按钮。 单步前进 (**F10**，或**转到下一个调用**导航线中。 粉红色的行现在变为 `j = AddInt(j);` 行。 **F10**在这种情况下不会单步执行到下一行代码。 相反，它将单步执行到下一个函数调用。 历史调试在调用之间进行导航，并跳过不包括函数调用的代码行。  
  
7.  现在单步执行到 `AddInt()` 方法。 应该立即看到此代码中的 Bug。  

## <a name="next-steps"></a>后续步骤

此过程仅粗略介绍使用历史调试可以执行的操作。

- 若要查看在调试时的快照，请参阅[查看快照使用 IntelliTrace 步骤回](../debugger/how-to-use-intellitrace-step-back.md)。
- 若要了解有关不同设置和导航线中不同按钮的效果的详细信息，请参阅[IntelliTrace 功能](../debugger/intellitrace-features.md)。