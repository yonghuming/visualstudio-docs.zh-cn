---
title: "Office 中的线程支持 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2157
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbfccabe310732943a818515c69abc61bec59e52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="threading-support-in-office"></a>Office 中的线程支持
  本主题提供有关如何线程处理在 Microsoft Office 对象模型中支持的信息。 Office 对象模型不是线程安全的但可以使用的 Office 解决方案中的多个线程。 Office 应用程序是组件对象模型 (COM) 服务器。 COM 允许客户端在任意线程上调用 COM 服务器。 对于不是线程安全的 COM 服务器，COM 提供了一种机制来序列化并发调用，以便在服务器上执行任何时候只有一个逻辑线程。 此机制称为单线程单元 (STA) 模型。 调用序列化，因为调用方可能会被阻塞的时间段时服务器太忙或正在处理其他后台线程上的调用。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>使用多个线程时所需的知识  
 若要使用的多个线程，你必须至少基本知识的以下方面的多线程处理：  
  
-   Windows Api  
  
-   COM 多线程的概念  
  
-   并发  
  
-   同步  
  
-   封送处理  
  
 有关常规信息有关的多线程处理，请参阅[托管线程处理](/dotnet/standard/threading/)。  
  
 在主 STA 中运行 office 了解其含义使可以了解如何使用用于 Office 的多个线程。  
  
## <a name="basic-multithreading-scenario"></a>多线程处理的基本方案  
 在 Office 解决方案中的代码始终在主 UI 线程上运行。 你可能想要通过在后台线程上运行单独的任务消除应用程序性能。 目标是完成两个任务看似同时而不是跟另一个，这应该产生更流畅的执行 （的主要原因要使用多个线程） 中的一个任务。 例如，你可能能够事件代码上的主的 Excel UI 线程，并且可能会在后台线程上运行的任务以从服务器收集数据，并使用来自服务器的数据更新 Excel 用户界面中的单元格。  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>调入 Office 对象模型的后台线程  
 当后台线程调用到 Office 应用程序时，但调用自动封送跨 STA 边界中。 但是，没有无法保证 Office 应用程序能够处理时后台线程进行的调用。 有几种可能性：  
  
1.  Office 应用程序必须发送调用以有机会输入的信息。 如果它正在执行大量处理，但不产生结果，则可能需要时间。  
  
2.  如果另一个逻辑线程单元中已存在，无法输入新线程。 这通常发生在逻辑线程进入 Office 应用程序，并将返回到调用方的单元的可重入调用。 阻止应用程序等待该调用返回。  
  
3.  Excel 可能处于状态，以便它无法立即处理的传入呼叫。 例如，Office 应用程序可能会显示一个模式对话框。  
  
 对于 2 和 3 的可能性，COM 提供[IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248)接口。 通过服务器实现它，如果输入的所有调用[HandleIncomingCall](http://msdn.microsoft.com/en-us/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be)方法。 有关第 2 种可能性，调用将自动被拒绝。 对于 3 种可能性，服务器可以拒绝的调用，取决于具体情况。 如果调用被拒绝，调用方必须决定要执行的操作。 通常情况下，调用方实现[IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248)，在这种情况下它将通过拒绝的通知[RetryRejectedCall](http://msdn.microsoft.com/en-us/3f800819-2a21-4e46-ad15-f9594fac1a3d)方法。  
  
 但是，对于通过使用 Visual Studio 中的 Office 开发工具创建解决方案，COM 互操作将转换到的所有被拒绝的调用<xref:System.Runtime.InteropServices.COMException>（"消息筛选器指示应用程序正在忙于"）。 每当进行调用的对象模型在后台线程，你必须在要准备好处理此异常。 通常，这涉及一定的时间重试，然后显示一个对话框。 但是，你还可以创建 STA 在后台线程，然后注册该线程来处理这种情况下一个消息筛选器。  
  
## <a name="starting-the-thread-correctly"></a>正确启动线程  
 当你创建新的 STA 线程时，设置为 STA 单元状态，启动线程之前。 下面的代码示例演示如何执行此操作。  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 有关详细信息，请参阅[托管线程处理的最佳做法](/dotnet/standard/threading/managed-threading-best-practices)。  
  
## <a name="modeless-forms"></a>无模式的窗体  
 无模式的窗体允许某种类型的与应用程序的交互，而该窗体显示。 在用户交互处理该窗体，并与无需关闭应用程序交互的窗体。 Office 对象模型支持托管的无模式窗体;但是，它们不应在后台线程上。  
  
## <a name="see-also"></a>另请参阅  
 [托管线程处理](/dotnet/standard/threading/)  
 [线程处理 (C#)](/dotnet/csharp/programming-guide/concepts/threading/index) [线程处理 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [使用线程与线程处理](/dotnet/standard/threading/using-threads-and-threading)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)  
  
  