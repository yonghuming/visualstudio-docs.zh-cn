---
title: "如何： 管理多个线程在托管代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 21fcc9388b40baa9e003b4beb876ba2f0f23fbaf
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>如何： 管理多个线程在托管代码
如果你有一个托管的 VSPackage 扩展调用异步方法或已在 Visual Studio UI 线程外的线程执行的操作，则应遵循下面给出的准则。 你可以让 UI 线程设置为保持响应状态，因为它不需要等待上另一个线程完成的工作。 你会使代码更高效，因为你不具有额外的线程占用堆栈空间，并且可以更加可靠且更易于调试，因为你避免死锁和挂起使。  
  
 一般情况下，可以从 UI 线程切换到另一个线程，反之亦然。 方法返回时，当前线程将是从中它最初调用的线程。  
  
> [!IMPORTANT]
>  以下准则使用中的 Api<xref:Microsoft.VisualStudio.Threading>命名空间，特别是，<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>类。 此命名空间中的 Api 是中的新增[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]。 你可以获取其实例<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>从<xref:Microsoft.VisualStudio.Shell.ThreadHelper>属性`ThreadHelper.JoinableTaskFactory`。  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>从 UI 线程切换到后台线程  
  
1.  如果在 UI 线程，并且你想要执行后台线程上的异步工作，使用 Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  如果你是在 UI 线程上，并且你想要以同步方式阻止后台线程，使用在执行工作时<xref:System.Threading.Tasks.TaskScheduler>属性`TaskScheduler.Default`内<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>从后台线程切换到 UI 线程  
  
1.  如果要在后台线程上，并且你想要在 UI 线程，使用上实现某些<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     你可以使用<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>方法以切换到 UI 线程。 此方法将消息发送到当前的异步方法中，延续的用户界面线程，还可与线程处理的框架，设置正确的优先级并避免死锁的其余部分通信。  
  
     如果你的后台线程方法不异步并且不能进行异步，仍可以使用`await`语法通过包装你的工作与切换到 UI 线程<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>，如下例所示：  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
