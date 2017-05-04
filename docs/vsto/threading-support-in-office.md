---
title: "Office 中的线程支持 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "多线程 [Visual Studio 中的 Office 开发]"
  - "对象模型 [Visual Studio 中的 Office 开发], 线程处理支持"
  - "Office 应用程序 [Visual Studio 中的 Office 开发], 线程处理支持"
  - "线程处理 [Visual Studio 中的 Office 开发]"
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2157
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Office 中的线程支持
  本主题提供有关如何在 Microsoft Office 对象模型中支持线程处理的信息。  Office 对象模型不是线程安全的，但可在 Office 解决方案中用于多个线程。  Office 应用程序是组件对象模型 \(COM\) 服务器。  COM 允许客户端在任意线程上调用 COM 服务器。  对于并非线程安全的 COM 服务器，COM 提供一种序列化并发调用的机制，这样无论何时服务器上都只有一个逻辑线程在执行。  此机制称为单线程单元 \(STA\) 模型。  因为调用是序列化的，所以服务器正忙时或处理后台线程上的其他调用时调用方可能会被阻塞一段时间。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 使用多线程必备的知识  
 若要使用多个线程，您必须至少具备以下方面的多线程处理基本知识：  
  
-   Windows API  
  
-   COM 多线程概念  
  
-   并发  
  
-   同步  
  
-   封送处理  
  
 有关多线程处理的常规信息，请参见[组件中的多线程处理](../Topic/Multithreading%20in%20Components.md)。  
  
 Office 运行于主 STA 中。  了解其含义有助于理解如何通过 Office 使用多个线程。  
  
## 基本的多线程处理方案  
 Office 解决方案中的代码始终在主 UI 线程上运行。  您可能想在一个后台线程上运行一个单独的任务，以使应用程序性能变得平稳。  其目标是让人们觉得好像是在同时完成两个任务，而不是一个完成之后再完成另一个，从而将导致执行更加平稳（这是使用多线程的主要原因）。  例如，您可能将事件代码放在 Excel UI 主线程上，而在后台线程上运行一个从服务器收集数据并且使用来自服务器的数据更新 Excel UI 中的单元格的任务。  
  
## 调入 Office 对象模型的后台线程  
 当一个后台线程调用 Office 应用程序时，将会跨 STA 边界自动封送该调用。  但是，无法保证后台线程进行调用时 Office 应用程序能够处理该调用。  存在多种可能性：  
  
1.  Office 应用程序必须发送调用的信息才能具有进入的机会。  如果它进行大量处理而不产生结果，则可能需要很长时间。  
  
2.  如果单元中已经存在其他逻辑线程，则新的线程会无法进入。  这通常发生在逻辑线程进入 Office 应用程序然后对调用方单元执行可重入回调的时候。  应用程序在等待调用返回时被阻止。  
  
3.  Excel 可能处于无法立即处理传入的调用的状态。  例如，Office 应用程序可能将显示一个模式对话框。  
  
 对于第 2 和第 3 种可能性，COM 提供了 [IMessageFilter](http://msdn.microsoft.com/zh-cn/e12d48c0-5033-47a8-bdcd-e94c49857248) 接口。  如果服务器实现该接口，则所有调用都可通过 [HandleIncomingCall](http://msdn.microsoft.com/zh-cn/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be) 方法进入。  对于第 2 种可能性，调用会被自动拒绝。  对于第 3 种可能性，服务器可以根据情况拒绝调用。  如果调用被拒绝，调用方必须确定下一步操作。  通常情况下，调用方实现 [IMessageFilter](http://msdn.microsoft.com/zh-cn/e12d48c0-5033-47a8-bdcd-e94c49857248)，这样，[RetryRejectedCall](http://msdn.microsoft.com/zh-cn/3f800819-2a21-4e46-ad15-f9594fac1a3d) 方法会通知它调用遭到拒绝。  
  
 但是，在使用 Visual Studio 中的 Office 开发工具创建解决方案的情况下，COM 互操作会将所有遭到拒绝的调用转换为 <xref:System.Runtime.InteropServices.COMException>（“消息筛选器指示应用程序正忙”）。  每次对后台线程执行对象模型调用时，都必须准备好处理此异常。  通常，这涉及重试一段时间然后显示对话框。  但是，也可以将后台线程作为 STA 创建，然后为该线程注册消息筛选器以处理此情况。  
  
## 正确地启动线程  
 在创建新的 STA 线程时，应在启动线程之前将单元状态设置为 STA。  下面的代码示例演示如何执行此操作。  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/ThisWorkbook.vb#5)]  
  
 有关更多信息，请参见[Managed Threading Best Practices](../Topic/Managed%20Threading%20Best%20Practices.md)。  
  
## 无模式窗体  
 无模式窗体允许在显示窗体时与应用程序进行某种类型的交互。  用户与窗体交互，窗体无需关闭就能与应用程序交互。  Office 对象模型支持托管的无模式窗体；但是，不应该在后台线程上使用这些窗体。  
  
## 请参阅  
 [组件中的多线程处理](../Topic/Multithreading%20in%20Components.md)   
 [Managed Threading](../Topic/Managed%20Threading.md)   
 [线程处理（C&#35; 和 Visual Basic）](../Topic/Threading%20(C%23%20and%20Visual%20Basic).md)   
 [Using Threads and Threading](../Topic/Using%20Threads%20and%20Threading.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)  
  
  