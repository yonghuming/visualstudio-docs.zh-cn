---
title: "“Microsoft Visual Studio 调试器（引发异常）”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exceptions.thrown"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "“Microsoft Visual Studio 调试器（引发异常）”对话框"
  - "异常处理，在调试期间"
  - "调试器，异常"
  - "引发异常，在调试期间"
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “Microsoft Visual Studio 调试器（引发异常）”对话框
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

程序中发生了异常。  此对话框报告引发异常的类型。  您的代码需要处理此异常。  可从下列用于处理异常的选项中进行选择：  
  
 **Break**  
 允许执行中断调试器。  在中断之前不调用异常处理程序。  如果您从中断继续执行，则将调用异常处理程序。  
  
 **Continue**  
 允许执行继续，并使异常处理程序有机会处理异常。  此选项对某些类型的异常不可用。  **“继续”**将允许应用程序继续。  在本机应用程序中，它将导致再次引发异常。  在托管应用程序中，它使程序终止或由宿主应用程序处理异常。  
  
> [!NOTE]
>  在托管代码中出现未经处理的异常后将无法继续。  在托管代码中出现未经处理的异常后选择**“继续”**将导致调试停止。  
  
 **忽略**  
 允许执行继续，但不调用异常处理程序。  由于未调用异常处理程序，这会导致更严重的后果，包括更多的异常和错误。  此选项对某些类型的异常不可用。  
  
## 请参阅  
 [管理调试器的异常](../debugger/managing-exceptions-with-the-debugger.md)   
 [异常的最佳做法](../Topic/Best%20Practices%20for%20Exceptions.md)   
 [异常处理](/visual-cpp/windows/exception-handling-cpp-component-extensions)