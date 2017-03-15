---
title: "如何︰ 管理多个线程在托管代码 |Microsoft 文档"
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
translationtype: Machine Translation
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: 417dc6e5285859424dfa3b482a90f1a141cff163
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>如何︰ 管理多个线程在托管代码
如果您有托管的 VSPackage 扩展调用异步方法的或具有在 Visual Studio UI 线程以外的线程执行的操作，应该遵循下面给出的准则。 因为它不需要等待上另一个线程来完成的工作，可以使 UI 线程保持响应状态。 您可以使您的代码更加有效，因为您不需要额外的线程会占用堆栈空间，您可以使它更加可靠和更轻松地调试，因为您可以避免死锁和挂起。  
  
 一般情况下，可以从 UI 线程切换到另一个线程，反之亦然。 方法返回时，当前线程是从中它最初调用的线程。  
  
> [!IMPORTANT]
>  以下准则<xref:Microsoft.VisualStudio.Threading>命名空间，尤其是，<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>类</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory></xref:Microsoft.VisualStudio.Threading>中使用的 Api 此命名空间中的 Api 是中的新增功能[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]。 您可以获取其实例<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>从<xref:Microsoft.VisualStudio.Shell.ThreadHelper>属性`ThreadHelper.JoinableTaskFactory`。</xref:Microsoft.VisualStudio.Shell.ThreadHelper> </xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>从 UI 线程切换到后台线程  
  
1.  如果你是在 UI 线程上，并且想要执行后台线程上的异步工作，使用 Task.Run():  
  
    ```c#  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  如果您是在 UI 线程上，并且你想要以同步方式阻止在后台线程，使用在执行工作时<xref:System.Threading.Tasks.TaskScheduler>属性`TaskScheduler.Default`内<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>::</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> </xref:System.Threading.Tasks.TaskScheduler>  
  
    ```c#  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>从后台线程切换到 UI 线程  
  
1.  如果您在后台线程上，并且您要做些什么在 UI 线程上，应使用<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>::</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>  
  
    ```c#  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     您可以使用<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>方法才能切换到 UI 线程。</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 此方法将消息发送到具有当前的异步方法的延续任务的 UI 线程，还可与设置正确的优先级并避免死锁的线程框架的其余部分通信。  
  
     如果您的后台线程方法不是异步，并且您不能进行异步，仍可以使用`await`语法通过包装您的工作与切换到 UI 线程<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>，如下例所示︰</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>  
  
    ```c#  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
