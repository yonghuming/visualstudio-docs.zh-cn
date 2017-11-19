---
title: "管理 Visual Studio 调试器的异常 |Microsoft 文档"
ms.custom: 
ms.date: 04/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0504ba8229e67284d4f54032dbbce3cef42d6e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>管理 Visual Studio 中的调试器异常

异常是执行程序时发生的错误状态的指示。 你可以让调试器在哪些异常 （或异常组） 上，中断并想要调试器中断的位置 （当调试器中断，它为你显示其中引发异常）。 你还可以添加或删除的异常。 使用 Visual Studio 中打开解决方案中，使用**调试 > Windows > 异常设置**以打开**异常设置**窗口。 

你可以并且应该提供响应最重要的异常的处理程序，但务必要了解如何配置调试器始终中断执行的某些异常。
  
异常发生时，调试程序将一条异常消息写入到输出窗口。 它可能会在以下情况中中断执行：  
  
-   引发异常且未进行处理时。  
  
-   当调试器配置为在调用任何处理之前中断执行。  
  
-   如果设置了[仅我的代码](../debugger/just-my-code.md)，且调试器配置为出现任何未在用户代码中处理的异常中断。  
  
> [!NOTE]
>  ASP.NET 有一个顶级异常处理程序，可以在浏览器中显示错误页。 除非启用 **“仅我的代码”** ，否则它不会中断执行。 有关示例，请参阅以下 [Setting the debugger to continue on user-unhandled exceptions](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) 。  
  
> [!NOTE]
>  在 Visual Basic 应用程序，调试器管理所有错误作为异常，即使你使用错误样式错误处理程序。    
  
## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>让调试器在引发异常时中断  
调试程序可以在引发异常的位置中断执行，这让你有机会在调用处理程序之前对异常进行检查。  
  
在**异常设置**窗口 (**调试 > Windows > 异常设置**)，展开某个类别的异常的节点 (例如，**公共语言运行时异常**，表示.NET 异常)，并选中该类别内特定异常的复选框 (例如**System.AccessViolationException**)。 还可以选择整个类别的异常。  
  
![选中 AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  

> [!TIP]
> 可以使用 **“异常设置”** 工具栏中的 **“搜索”** 窗口查找特定窗口，或使用搜索筛选特定命名空间（例如， **System.IO**）。
  
如果选择中的出现异常**异常设置**窗口中，调试器将中断执行引发异常，无论它是在处理还是在未经处理的任何位置。 此时，该异常被称为第一次机会异常。 以下是几个应用场景示例：  
  
*  在下面的 C# 控制台应用程序中，Main 方法将在 **try/catch** 块内引发 `try/catch` ：  
  
    ```CSharp  
    static void Main(string[] args)  
    {  
        try  
        {  
            throw new AccessViolationException();  
            Console.WriteLine("here");  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("caught exception");  
        }  
        Console.WriteLine("goodbye");  
    }  
    ```  
  
     如果在“异常设置” **try/catch** 中选中了 **“异常设置”**，则在调试程序中运行此代码时，执行将在 `throw` 行上中断。 然后可以继续执行。 控制台应显示这两行：  
  
    ```  
    caught exception  
    goodbye  
    ```  
  
     但它没有显示 `here` 行。  
  
*  C# 控制台应用程序引用的类库具有两个方法、 引发异常，并对其进行处理的方法和一个引发同一异常并不会处理它的第二个方法的类：  
  
    ```csharp 
    public class Class1  
    {  
        public void ThrowHandledException()  
        {  
            try  
            {  
                throw new AccessViolationException();  
            }  
            catch (AccessViolationException ave)  
            {  
                Console.WriteLine("caught exception" + ave.Message);  
            }  
        }  
  
        public void ThrowUnhandledException()  
        {  
            throw new AccessViolationException();  
        }  
    }  
    ```  
  
     下面是控制台应用程序的 main （） 方法：  
  
    ```CSharp  
    static void Main(string[] args)  
    {  
        Class1 class1 = new Class1();  
        class1.ThrowHandledException();  
        class1.ThrowUnhandledException();  
    }  
    ```  
  
     如果在“异常设置” **try/catch** 中选中了 **“异常设置”**，则在调试程序中运行此代码时，执行将在 `throw` 和 **ThrowUnhandledException()** 中的 **throw**，以在打开解决方案时打开此窗口。  
  
 如果想要将异常设置还原为默认值，则可以单击工具栏上的 **“还原”** 按钮：  
  
 ![还原异常设置中的默认值](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
##  <a name="BKMK_UserUnhandled"></a>让调试器在遇到用户未经处理异常时继续  
 如果正在使用 [Just My Code](../debugger/just-my-code.md)调试 .NET 或 JavaScript 代码，则对于未在用户代码中进行处理但在其他地方进行了处理的异常，可以让调试程序不要执行中断操作。  
  
1.  在 **“异常设置”** 窗口中，通过在窗口中右键单击打开上下文菜单，然后选择 **“显示列”**。 （如果已禁用 **“仅我的代码”**，则将看不到此命令。）  
  
2.  应该看到名为 **“其他操作”**的第二个列。 此列对特定异常显示 **“在用户代码中未经处理时继续操作”** ，这意味着对于未在用户代码中进行处理但在其他地方进行了处理的异常，调试程序不会执行中断操作。  
  
3.  可以为特定异常（选择异常，右键单击，然后选择/取消选择 **“在用户代码中未经处理时继续操作”**）或为整个类别的异常（例如，所有公共语言运行时异常）更改此设置。  
  
 例如，ASP.NET Web 应用程序通过将异常转换为 HTTP 500 状态代码来处理异常（[ASP.NET API 中的异常处理](http://www.asp.net/web-api/overview/error-handling/exception-handling)），该方法可能无法帮助你确定异常的源。 在下面的示例中，用户代码对引发 `String.Format()` 的 <xref:System.FormatException>进行调用。 异常中断如下所示：  
  
 ![位置中断用户 &#45; 分隔符异常](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
## <a name="add-and-delete-exceptions"></a>添加和删除异常  
 可以添加和删除异常。 通过选择异常并单击 **“异常设置”** 工具栏上的 **“删除”** 按钮，或右键单击异常并从上下文菜单选择 **“删除”** ，可以从任何类别删除任何类型的异常。 删除异常与取消选中异常的效果一样，即调试程序在该异常被引发时将不会执行中断操作。  
  
 添加异常：在 **“异常设置”** 窗口中，选择其中一个异常类别（例如， **“公共语言运行时”**），然后单击 **“添加”** 按钮。 键入异常的名称（例如， **System.UriTemplateMatchException**）。 异常会添加到列表（按字母顺序），并会被自动选中。  
  
 如果想要将异常添加到 GPU 内存访问异常、JavaScript 运行时异常或 Win32 异常类别，则需要包括错误代码和说明。  
  
> [!TIP]
>  请检查你的拼写！ **异常设置**窗口不会检查是否存在添加的异常。 因此，如果键入**Sytem.UriTemplateMatchException**，则将获得该异常的条目 (而不是针对**System.UriTemplateMatchException**)。  
  
 异常设置保留在解决方案的.suo 文件中，因此它们适用于特定解决方案。 你无法跨解决方案重用特定异常设置。 此时，仅保留添加的异常，而不会保留删除的异常。 换而言之，可以添加一个异常，然后关闭并重新打开解决方案，该异常将仍然存在。 但是，如果删除一个异常，然后关闭/重新打开解决方案，异常将消失。  
  
 **“异常设置”** 窗口在 C# 中支持通用异常类型，但在 Visual Basic 中不支持。 要对类似 `MyNamespace.GenericException<T>`的异常执行中断操作，则必须将异常作为 **MyNamespace.GenericException`1**添加。 也就是说，如果已经创建如下所示的异常：  
  
```CSharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 则可以按照如下所示方式将异常添加到 **“异常设置”** 窗口中：  
  
 ![添加常见异常](../debugger/media/addgenericexception.png "AddGenericException")  

## <a name="add-conditions-to-an-exception"></a>将条件添加到异常

你可以设置条件中的异常上**异常设置**对话框。 当前支持的条件包括用于包含或排除异常的模块名称。 通过将模块名称设置为条件，你可以选择仅在特定代码模块上异常中断或可以避免在特定的模块上的换行。

> [!NOTE]
> 将条件添加到异常是中的新增功能[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

若要添加条件异常，请选择**编辑条件**图标异常设置对话框框中或右键单击异常并选择**编辑条件**。

![关于异常的条件](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")
  
## <a name="see-also"></a>另请参阅  
 [在出现异常之后继续执行](../debugger/continuing-execution-after-an-exception.md)   
 [如何： 出现异常后检查系统代码](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [如何： 使用本机运行时检查](../debugger/how-to-use-native-run-time-checks.md)   
 [使用无 C 运行库运行时检查](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [调试器基础知识](../debugger/debugger-basics.md)