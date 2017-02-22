---
title: "如何：调试 ASP.NET 异常 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, 异常"
  - "调试 [Visual Studio], ASP.NET 异常"
  - "异常, ASP.NET"
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：调试 ASP.NET 异常
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

调试异常是开发可靠的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应用程序的重要一步。  有关如何调试异常的常规信息，请参见[管理调试器的异常](../debugger/managing-exceptions-with-the-debugger.md)。  
  
 若要调试未处理的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 异常，必须确保调试器能够在发生这些异常时停止。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 运行时有一个顶级异常处理程序。  因此，默认情况下，调试器绝不会在未经处理的异常中中断。  若要在引发异常时中断调试器，必须在**“异常”**对话框中为该特定的异常选择**“发生以下异常时中断: 引发”**设置。  
  
 如果已启用“仅我的代码”，则当 .NET Framework 方法或其他系统代码中引发异常时，**“发生以下异常时中断: 引发”**不会导致调试器立即中断。  执行将继续，直至调试器命中非系统代码时才中断。  因此，不必在发生异常时逐句通过系统代码。  
  
 “仅我的代码”向您提供了另一个可能更有用的选项：**“发生以下异常时中断: 用户未处理的”**。  如果为异常选择此设置，则调试器将在用户代码中中断执行，但是仅当异常没有被用户代码捕获和处理时，它才这样做。  此设置会使顶级 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 异常处理程序不起作用，因为该处理程序位于非用户代码中。  
  
### 启用 ASP.NET 异常调试和“仅我的代码”  
  
1.  在**“调试”**菜单上，单击**“异常”**。  
  
     将出现**“异常”**对话框。  
  
2.  在**“公共语言运行时异常”**行上，选择**“引发”**或**“用户未处理的”**。  
  
     若要使用**“用户未处理的”**设置，必须启用**“仅我的代码”**。  
  
### 采用 ASP.NET 异常处理的最佳做法  
  
-   在可能引发您知道如何处理的可预见异常的代码周围放置 `try … catch` 块。  例如，如果应用程序调用 XML Web services 或直接调用 SQL Server，则应该将该代码置于 **try … catch** 块中，因为此过程中可能会发生大量异常。