---
title: "调试 ASP.NET 和 AJAX 应用程序 | Microsoft Docs"
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
  - "调试 [ASP.NET], 关于 ASP.NET 调试"
  - "调试 ASP.NET Web 应用程序"
  - "调试, WCF"
  - "WCF, 调试"
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 调试 ASP.NET 和 AJAX 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

调试 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序类似于调试 Windows 窗体或任何其他 Windows 应用程序，因为这两种应用程序都涉及到控件和事件。  但是，Web 应用程序与 Windows 应用程序之间还有一些基本差异：  
  
-   在 Web 应用程序中跟踪状态更为复杂。  
  
-   在 Windows 应用程序中，要调试的代码几乎全部位于一个位置；而在 Web 应用程序中，该代码可以分别位于客户端和服务器上。  虽然 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 代码全都在服务器上，但在客户端上可能还有 JavaScript 或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 代码。  
  
## 本节内容  
 [调试 ASP.NET 的准备工作](../debugger/preparing-to-debug-aspnet.md)  
 描述启用 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应用程序调试所需的步骤。  
  
 [调试 Web 应用程序](../debugger/debugging-web-applications.md)  
 讨论如何调试 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应用程序，包括启用 AJAX 的脚本应用程序。  
  
## 相关章节  
 [管理调试器的异常](../debugger/managing-exceptions-with-the-debugger.md)  
 说明调试 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 异常时必须启用“仅我的代码”的原因。  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)  
 讨论可帮助您调试 AJAX 代码的一些方法和工具。  
  
 [使用 IntelliTrace](../debugger/intellitrace.md)  
 使用 IntelliTrace 可记录和审阅应用程序的状态的历史记录而不用经常重新启动应用程序，从而加快了代码的调试速度。  您可以查看有关在运行应用程序期间发生的事件和调用的信息，然后在这些时间点上开始调试。  需要 Visual Studio Ultimate。  
  
## 请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试 Web 应用程序和脚本](../debugger/debugging-web-applications-and-script.md)   
 [调试设置和准备](../debugger/debugger-settings-and-preparation.md)   
 [调试器基础知识](../debugger/debugger-basics.md)