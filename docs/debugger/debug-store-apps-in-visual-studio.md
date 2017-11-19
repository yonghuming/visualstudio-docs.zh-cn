---
title: "调试 Visual Studio 中的 UWP 应用 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
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
ms.assetid: 48a85bcf-290b-4390-9993-f6f9dd73ad03
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3920bfbd5b1ddbddc3166118ead0c7d0fefff8d8
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="debug-uwp-apps-in-visual-studio"></a>调试 Visual Studio 中的 UWP 应用
你可以通过 Visual Studio 调试器控制程序的执行并检查其状态。 若要在 UWP 应用中查找出现缺陷的原因并了解完全如何应用正常工作时，可以使用调试器。 当在调试器中暂停（中断）执行时，Visual Studio 将显示源文件，该源文件包含执行代码并突出显示执行语句。 可以查看变量值、执行函数的调用堆栈以及程序状态的其他方面。 一次可使用一个语句来继续执行（分步完成）程序，以查看语句如何更改该程序的值。 在使用 JavaScript 编写的应用中，你可以检查并操作页面的 DOM。  
  
## <a name="in-this-section"></a>本节内容  
  
|||  
|-|-|  
|[启动调试会话 (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)|“如何启动调试会话”描述了用于针对 JavaScript 应用配置和启动调试会话的不同选项。|  
|[调试会话 (JavaScript) 中控制执行](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)|调试器导航将通过简单的应用来演示如何启动和停止调试、如何在代码中导航以及如何查看程序状态。|  
|[快速入门：调试 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)|调试 HTML 和 CSS 演示了如何使用实时 DOM 检查工具以交互方式调试 JavaScript 应用，以查看和修改 HTML 和 CSS。|  
|[快速入门： 调试 JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)|使用控制台调试 JavaScript 演示如何以交互方式调试 JavaScript 应用使用[JavaScript 控制台命令](../debugger/javascript-console-commands.md)。|  
|[启动调试会话 (VB、 C#、 c + + 和 XAML）](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)|“如何启动调试会话（Visual C++、Visual C# 和 Visual Basic）”描述了用于针对应用（使用 Visual C++、Visual C# 或 Visual Basic 编写而成）配置和启动调试会话的不同选项。|  
|[导航调试会话 （Xaml 和 C#）](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)|调试器导航将通过简单的应用来演示如何启动和停止调试、如何在代码中导航以及如何查看和更改程序状态。|  
|[触发挂起、 继续和后台适用于 UWP 应用的事件)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)|调试器将禁用挂起、继续和终止应用的 Windows 进程生命期管理 (PLM) 事件。 你可以从调试器工具栏触发这些事件。<br /><br /> 通过后台任务，可执行某些重要操作，即便应用已挂起也是如此。 调试器使你能够启动并调试这些后台任务。|  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中进行调试](../debugger/index.md)  
 [（在 MSDN 库中） 的调试器功能教程](http://go.microsoft.com/fwlink/?LinkID=226896)